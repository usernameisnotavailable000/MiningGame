using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Timers;
using System.Net;
using System.IO;
using System.Windows.Forms;

namespace WindowsFormsApp1
{
    
    public partial class MiningGame : Form
    {
        int num = -1;
        int phase = 0;
        bool autoC = false;



        public MiningGame()
        {
            InitializeComponent();
            this.mining.Click += BtnMining;
            this.upgrade.Click += BtnUpgrade;
            this.autoClick.Click += AutoClicker;
        }

        private void Form1_Load(object sender, EventArgs e)
        {
            if (phase == 0) // 돌 곡괭이
            {
                num++;
            }
            else if (phase == 1) // 청동 곡괭이
            {
                num += 2;
            }
            else if (phase == 2) // 강철 곡괭이
            {
                num += 4;
            }
            else if (phase == 3) // 은 곡괭이
            {
                num += 8;
            }
            else if (phase == 4) // 금 곡괭이
            {
                num += 16;
            }
            else if (phase == 5) // 다이아 곡괭이
            {
                num += 32;
            }
            else if (phase == 6) // 전설의 곡괭이
            {
                num += 64;
            }

            string stone = num.ToString();
            result.Text = stone + " 광석";
        }

        private void BtnMining(object sender, EventArgs e)
        {
            if (phase == 0) // 돌 곡괭이
            {
                num++;
            }
            else if (phase == 1) // 청동 곡괭이
            {
                num += 2;
            }
            else if (phase == 2) // 강철 곡괭이
            {
                num += 4;
            }
            else if (phase == 3) // 은 곡괭이
            {
                num += 8;
            }
            else if (phase == 4) // 금 곡괭이
            {
                num += 16;
            }
            else if (phase == 5) // 다이아 곡괭이
            {
                num += 32;
            }
            else if (phase == 6) // 전설의 곡괭이
            {
                num += 64;
            }

            string stone = num.ToString();
            result.Text = stone + " 광석";
        }

        private void BtnUpgrade(object sender, EventArgs e)
        {
            if(phase == 0)
            {
                if(num >= 200)
                {
                    phase++;
                    num -= 200;
                    pickaxe.Text = "청동 곡괭이";
                    upgrade.Text = "곡괭이 강화 (1000 광석)";
                    MessageBox.Show("곡괭이가 강화되었습니다!");
                }
                else
                {
                    MessageBox.Show("광석이 부족합니다!");
                }
            }
            else if (phase == 1)
            {
                if (num >= 1000)
                {
                    phase++;
                    num -= 1000;
                    pickaxe.Text = "강철 곡괭이";
                    upgrade.Text = "곡괭이 강화 (5000 광석)";
                    MessageBox.Show("곡괭이가 강화되었습니다!");
                }
                else
                {
                    MessageBox.Show("광석이 부족합니다!");
                }
            }
            else if (phase == 2)
            {
                if (num >= 5000)
                {
                    phase++;
                    num -= 5000;
                    pickaxe.Text = "은 곡괭이";
                    upgrade.Text = "곡괭이 강화 (25000 광석)";
                    MessageBox.Show("곡괭이가 강화되었습니다!");
                }
                else
                {
                    MessageBox.Show("광석이 부족합니다!");
                }
            }
            else if (phase == 3)
            {
                if (num >= 25000)
                {
                    phase++;
                    num -= 25000;
                    pickaxe.Text = "금 곡괭이";
                    upgrade.Text = "곡괭이 강화 (100000 광석)";
                    MessageBox.Show("곡괭이가 강화되었습니다!");
                }
                else
                {
                    MessageBox.Show("광석이 부족합니다!");
                }
            }
            else if (phase == 4)
            {
                if (num >= 100000)
                {
                    phase++;
                    num -= 100000;
                    pickaxe.Text = "다이아 곡괭이";
                    upgrade.Text = "곡괭이 강화 (999999 광석)";
                    MessageBox.Show("곡괭이가 강화되었습니다!");
                }
                else
                {
                    MessageBox.Show("광석이 부족합니다!");
                }
            }
            else if (phase == 5)
            {
                if (num >= 999999)
                {
                    phase++;
                    num -= 999999;
                    pickaxe.Text = "전설의 곡괭이";
                    upgrade.Text = "강화 완료!";
                    upgrade.Enabled = false;
                    MessageBox.Show("곡괭이가 강화되었습니다!");
                }
                else
                {
                    MessageBox.Show("광석이 부족합니다!");
                }
            }

            string stone = num.ToString();
            result.Text = stone + " 광석";
        }

        private void AutoClicker(object sender, EventArgs e)
        {
            if(autoC == false)
            {
                autoClick.Text = "수동 캐기";
                autoC = true;
                mining.Enabled = false;
                timer1.Enabled = true;
            }
            else if(autoC == true)
            {
                autoClick.Text = "자동 캐기";
                autoC = false;
                mining.Enabled = true;
                timer1.Enabled = false;
            }
        }
    }
}
