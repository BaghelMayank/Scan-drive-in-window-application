# Scan-drive-in-window-application
scan drives and count files
using System;
using System.IO;
using System.Windows.Forms;

namespace scanner
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
            panel1.Visible = true;
        }

        private void label1_Click(object sender, EventArgs e)
        {

        }

      

        private void comboBox1_SelectedIndexChanged(object sender, EventArgs e)
        {
            if(comboBox1.SelectedItem.ToString() =="Drive SCAN")
            {
                DriveInfo[] drive = DriveInfo.GetDrives();
                panel1.Visible = false;
                foreach (var d in drive)
                {
                    comboBox2.Items.Add(d.Name);
                }

            }
        }
        #region
        public void comboBox2_SelectedIndexChanged(object sender, EventArgs e)

        {
           
            if (comboBox2.SelectedItem.ToString() == @"C:\")
            {
                DirectoryInfo cdrive = new DirectoryInfo(@"C:\");
                int cdcount = cdrive.GetFiles().Length;


            }
        
        
        }

        private void panel1_Paint(object sender, PaintEventArgs e)
        {

        }

        private void textBox1_TextChanged(object sender, EventArgs e)
        {
           
        }
        #endregion
        private void button1_Click(object sender, EventArgs e)
        {
            if (comboBox1.SelectedItem.ToString()=="Full SCAN")
            {
                DirectoryInfo cdrive = new DirectoryInfo(@"C:\");
                int cdcount = cdrive.GetFiles().Length;
                DirectoryInfo ddrive = new DirectoryInfo(@"D:\");
                int ddcount = ddrive.GetFiles().Length;
                int tcount = ddcount + cdcount;
                MessageBox.Show(tcount.ToString(), "SCAN REPORT", MessageBoxButtons.OK, MessageBoxIcon.Information);
            }
            else if (comboBox2.SelectedItem.ToString() == @"C:\")
            {
                DirectoryInfo cdrive = new DirectoryInfo(@"C:\");
                int cdcount = cdrive.GetFiles().Length;
                MessageBox.Show(cdcount.ToString(),"SCAN REPORT",MessageBoxButtons.OK,MessageBoxIcon.Information);
            }
            else if (comboBox2.SelectedItem.ToString() == @"D:\")
            {
                DirectoryInfo cdrive = new DirectoryInfo(@"D:\");
                int cdcount = cdrive.GetFiles().Length;
                MessageBox.Show(cdcount.ToString(), "SCAN REPORT", MessageBoxButtons.OK, MessageBoxIcon.Information);
            }
           
            
        }
    }
}
