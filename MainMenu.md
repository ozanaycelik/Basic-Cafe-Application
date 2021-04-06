# Basic-Cafe-Application
Cafe application
using System;
using System.Collections;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Data.SqlClient;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace Kahvehane_Uygulaması
{
    public partial class AnaMenü : Form
    {
        public AnaMenü()
        {
            InitializeComponent();
        }

        private void AnaMenü_Load(object sender, EventArgs e)
        {
            // TODO: This line of code loads data into the 'kAHVEHANEDataSet.Urun_Fiyat' table. You can move, or remove it, as needed.
            //this.urun_FiyatTableAdapter.Fill(this.kAHVEHANEDataSet.Urun_Fiyat);
        }

        private void cbx_Sıcak_SelectedIndexChanged(object sender, EventArgs e)
        {

        }

        private void radioButton1_CheckedChanged(object sender, EventArgs e)
        {

        }

        static string tür = string.Empty;

        static int miktar = 0;

        static string toplam3 = string.Empty;

        string eleman = tür + miktar + toplam3;


        double toplam2 = 0;

        double toplam = 0;
        private void btn_Hesapla_Click(object sender, EventArgs e)
        {
            #region Kahve seçimleri
            if (cbx_Kahve.SelectedValue != "" && nud_kahve.Value != 0)
            {
                var kahve = cbx_Kahve.SelectedItem;
                decimal price = 0;
                switch (kahve)
                {
                    case "Misto":
                        price = 4.5m;
                        break;
                    case "Americano":
                        price = 5.75m;
                        break;
                    case "Bianco":
                        price = 6m;
                        break;
                    case "”Cappucino":
                        price = 7.5m;
                        break;
                    case "Macchiato":
                        price = 6.75m;
                        break;
                    case "Con Panna":
                        price = 8m;
                        break;
                    case "Mocha":
                        price = 7.75m;
                        break;
                    default:
                        break;
                }
                toplam = (double)price;

                if (cbx_1x.Checked == true && cbx_2x.Checked != true)
                {
                    toplam += 0.75;
                    if (rb_yagsiz.Checked == true)
                    {
                        toplam += 0.50;
                        toplam *= Convert.ToDouble(nud_kahve.Value);
                        eleman = "Yağsız süt x + 1x - " + cbx_Kahve.SelectedItem + " x " + nud_kahve.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_soya.Checked == true)
                    {
                        toplam += 0.50;
                        toplam *= Convert.ToDouble(nud_kahve.Value);
                        var eleman = "Soya süt x + 1x -  " + cbx_Kahve.SelectedItem + " x " + nud_kahve.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_grande.Checked == true)
                    {
                        toplam *= 1.25;
                        toplam *= Convert.ToDouble(nud_kahve.Value);
                        var eleman = "Grande Boy x + 1x -  " + cbx_Kahve.SelectedItem + " x " + nud_kahve.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_Venti.Checked == true)
                    {
                        toplam *= 1.75;
                        toplam *= Convert.ToDouble(nud_kahve.Value);
                        var eleman = "Venti Boy x  + 1x - " + cbx_Kahve.SelectedItem + " x " + nud_kahve.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_tall.Checked == true)
                    {
                        toplam *= 1;
                        toplam *= Convert.ToDouble(nud_kahve.Value);
                        var eleman = "Tall Boy x  + 1x - " + cbx_Kahve.SelectedItem + " x " + nud_kahve.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);

                    }
                    else
                    {
                        toplam *= 1;
                        toplam *= Convert.ToDouble(nud_kahve.Value);
                        var eleman = "Tall Boy x  + 1x - " + cbx_Kahve.SelectedItem + " x " + nud_kahve.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                }
                else if (cbx_1x.Checked == true && cbx_2x.Checked == true)
                {
                    toplam += (0.75 * 3);

                    if (rb_yagsiz.Checked == true)
                    {
                        toplam += 0.50;
                        toplam *= Convert.ToDouble(nud_kahve.Value);
                        var eleman = "Yağsız süt x + 3x - " + cbx_Kahve.SelectedItem + " x " + nud_kahve.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_soya.Checked == true)
                    {
                        toplam += 0.50;
                        toplam *= Convert.ToDouble(nud_kahve.Value);
                        var eleman = "Soya süt x + 3x -  " + cbx_Kahve.SelectedItem + " x " + nud_kahve.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_grande.Checked == true)
                    {
                        toplam *= 1.25;
                        toplam *= Convert.ToDouble(nud_kahve.Value);
                        var eleman = "Grande Boy x + 3x -  " + cbx_Kahve.SelectedItem + " x " + nud_kahve.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_Venti.Checked == true)
                    {
                        toplam *= 1.75;
                        toplam *= Convert.ToDouble(nud_kahve.Value);
                        var eleman = "Venti Boy x  + 3x - " + cbx_Kahve.SelectedItem + " x " + nud_kahve.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_tall.Checked == true)
                    {
                        toplam *= 1;
                        toplam *= Convert.ToDouble(nud_kahve.Value);
                        var eleman = "Tall Boy x  + 3x - " + cbx_Kahve.SelectedItem + " x " + nud_kahve.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);

                    }
                    else
                    {
                        toplam *= 1;
                        toplam *= Convert.ToDouble(nud_kahve.Value);
                        var eleman = "Tall Boy x  + 3x - " + cbx_Kahve.SelectedItem + " x " + nud_kahve.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                }
                else if (cbx_1x.Checked != true && cbx_2x.Checked == true)
                {
                    toplam += (0.75 * 2);

                    if (rb_yagsiz.Checked == true)
                    {
                        toplam += 0.50;
                        toplam *= Convert.ToDouble(nud_kahve.Value);
                        var eleman = "Yağsız süt x + 2x - " + cbx_Kahve.SelectedItem + " x " + nud_kahve.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_soya.Checked == true)
                    {
                        toplam += 0.50;
                        toplam *= Convert.ToDouble(nud_kahve.Value);
                        var eleman = "Soya süt x + 2x -  " + cbx_Kahve.SelectedItem + " x " + nud_kahve.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_grande.Checked == true)
                    {
                        toplam *= 1.25;
                        toplam *= Convert.ToDouble(nud_kahve.Value);
                        var eleman = "Grande Boy x + 2x -  " + cbx_Kahve.SelectedItem + " x " + nud_kahve.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_Venti.Checked == true)
                    {
                        toplam *= 1.75;
                        toplam *= Convert.ToDouble(nud_kahve.Value);
                        var eleman = "Venti Boy x  + 2x - " + cbx_Kahve.SelectedItem + " x " + nud_kahve.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_tall.Checked == true)
                    {
                        toplam *= 1;
                        toplam *= Convert.ToDouble(nud_kahve.Value);
                        var eleman = "Tall Boy x  + 2x - " + cbx_Kahve.SelectedItem + " x " + nud_kahve.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);

                    }
                    else
                    {
                        toplam *= 1;
                        toplam *= Convert.ToDouble(nud_kahve.Value);
                        var eleman = "Tall Boy x  + 2x - " + cbx_Kahve.SelectedItem + " x " + nud_kahve.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }


                }
                else
                {
                    if (rb_yagsiz.Checked == true)
                    {
                        toplam += 0.50;
                        toplam *= Convert.ToDouble(nud_kahve.Value);
                        var eleman = "Yağsız süt x " + cbx_Kahve.SelectedItem + " x " + nud_kahve.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_soya.Checked == true)
                    {
                        toplam += 0.50;
                        toplam *= Convert.ToDouble(nud_kahve.Value);
                        var eleman = "Soya süt x " + cbx_Kahve.SelectedItem + " x " + nud_kahve.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_grande.Checked == true)
                    {
                        toplam *= 1.25;
                        toplam *= Convert.ToDouble(nud_kahve.Value);
                        var eleman = "Grande Boy x " + cbx_Kahve.SelectedItem + " x " + nud_kahve.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_Venti.Checked == true)
                    {
                        toplam *= 1.75;
                        toplam *= Convert.ToDouble(nud_kahve.Value);
                        var eleman = "Venti Boy x " + cbx_Kahve.SelectedItem + " x " + nud_kahve.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_tall.Checked == true)
                    {
                        toplam *= 1;
                        toplam *= Convert.ToDouble(nud_kahve.Value);
                        var eleman = "Tall Boy x " + cbx_Kahve.SelectedItem + " x " + nud_kahve.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);

                    }
                    else
                    {
                        toplam *= 1;
                        toplam *= Convert.ToDouble(nud_kahve.Value);
                        var eleman = "Tall Boy x " + cbx_Kahve.SelectedItem + " x " + nud_kahve.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                }






            }

            #endregion

            #region soguk icecekler

            if (cbx_Soguk.SelectedValue != "" && nud_soguk.Value != 0)
            {
                toplam += 7.5;

                if (cbx_1x.Checked == true && cbx_2x.Checked != true)
                {
                    toplam += 0.75;
                    if (rb_yagsiz.Checked == true)
                    {
                        toplam += 0.50;
                        toplam *= Convert.ToDouble(nud_soguk.Value);
                        var eleman = "Yağsız süt x + 1x - " + cbx_Soguk.SelectedItem + " x " + nud_soguk.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_soya.Checked == true)
                    {
                        toplam += 0.50;
                        toplam *= Convert.ToDouble(nud_soguk.Value);
                        var eleman = "Soya süt x + 1x -  " + cbx_Soguk.SelectedItem + " x " + nud_soguk.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_grande.Checked == true)
                    {
                        toplam *= 1.25;
                        toplam *= Convert.ToDouble(nud_soguk.Value);
                        var eleman = "Grande Boy x + 1x -  " + cbx_Soguk.SelectedItem + " x " + nud_soguk.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_Venti.Checked == true)
                    {
                        toplam *= 1.75;
                        toplam *= Convert.ToDouble(nud_soguk.Value);
                        var eleman = "Venti Boy x  + 1x - " + cbx_Soguk.SelectedItem + " x " + nud_soguk.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_tall.Checked == true)
                    {
                        toplam *= 1;
                        toplam *= Convert.ToDouble(nud_soguk.Value);
                        var eleman = "Tall Boy x  + 1x - " + cbx_Soguk.SelectedItem + " x " + nud_soguk.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);

                    }
                    else
                    {
                        toplam *= 1;
                        toplam *= Convert.ToDouble(nud_soguk.Value);
                        var eleman = "Tall Boy x  + 1x - " + cbx_Soguk.SelectedItem + " x " + nud_soguk.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                }
                else if (cbx_1x.Checked == true && cbx_2x.Checked == true)
                {
                    toplam += (0.75 * 3);

                    if (rb_yagsiz.Checked == true)
                    {
                        toplam += 0.50;
                        toplam *= Convert.ToDouble(nud_soguk.Value);
                        var eleman = "Yağsız süt x + 3x - " + cbx_Soguk.SelectedItem + " x " + nud_soguk.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_soya.Checked == true)
                    {
                        toplam += 0.50;
                        toplam *= Convert.ToDouble(nud_soguk.Value);
                        var eleman = "Soya süt x + 3x -  " + cbx_Soguk.SelectedItem + " x " + nud_soguk.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_grande.Checked == true)
                    {
                        toplam *= 1.25;
                        toplam *= Convert.ToDouble(nud_soguk.Value);
                        var eleman = "Grande Boy x + 3x -  " + cbx_Soguk.SelectedItem + " x " + nud_soguk.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_Venti.Checked == true)
                    {
                        toplam *= 1.75;
                        toplam *= Convert.ToDouble(nud_soguk.Value);
                        var eleman = "Venti Boy x  + 3x - " + cbx_Soguk.SelectedItem + " x " + nud_soguk.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_tall.Checked == true)
                    {
                        toplam *= 1;
                        toplam *= Convert.ToDouble(nud_soguk.Value);
                        var eleman = "Tall Boy x  + 3x - " + cbx_Soguk.SelectedItem + " x " + nud_soguk.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);

                    }
                    else
                    {
                        toplam *= 1;
                        toplam *= Convert.ToDouble(nud_soguk.Value);
                        var eleman = "Tall Boy x  + 3x - " + cbx_Soguk.SelectedItem + " x " + nud_soguk.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                }
                else if (cbx_1x.Checked != true && cbx_2x.Checked == true)
                {
                    toplam += (0.75 * 2);

                    if (rb_yagsiz.Checked == true)
                    {
                        toplam += 0.50;
                        toplam *= Convert.ToDouble(nud_soguk.Value);
                        var eleman = "Yağsız süt x + 2x - " + cbx_Soguk.SelectedItem + " x " + nud_soguk.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_soya.Checked == true)
                    {
                        toplam += 0.50;
                        toplam *= Convert.ToDouble(nud_soguk.Value);
                        var eleman = "Soya süt x + 2x -  " + cbx_Soguk.SelectedItem + " x " + nud_soguk.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_grande.Checked == true)
                    {
                        toplam *= 1.25;
                        toplam *= Convert.ToDouble(nud_soguk.Value);
                        var eleman = "Grande Boy x + 2x -  " + cbx_Soguk.SelectedItem + " x " + nud_soguk.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_Venti.Checked == true)
                    {
                        toplam *= 1.75;
                        toplam *= Convert.ToDouble(nud_soguk.Value);
                        var eleman = "Venti Boy x  + 2x - " + cbx_Soguk.SelectedItem + " x " + nud_soguk.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_tall.Checked == true)
                    {
                        toplam *= 1;
                        toplam *= Convert.ToDouble(nud_soguk.Value);
                        var eleman = "Tall Boy x  + 2x - " + cbx_Soguk.SelectedItem + " x " + nud_soguk.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);

                    }
                    else
                    {
                        toplam *= 1;
                        toplam *= Convert.ToDouble(nud_soguk.Value);
                        var eleman = "Tall Boy x  + 2x - " + cbx_Soguk.SelectedItem + " x " + nud_soguk.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }


                }

                else
                {
                    if (rb_yagsiz.Checked == true)
                    {
                        toplam += 0.50;
                        toplam *= Convert.ToDouble(nud_soguk.Value);
                        var eleman = "Yağsız süt x " + cbx_Soguk.SelectedItem + " x " + nud_soguk.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_soya.Checked == true)
                    {
                        toplam += 0.50;
                        toplam *= Convert.ToDouble(nud_soguk.Value);
                        var eleman = "Soya süt x " + cbx_Soguk.SelectedItem + " x " + nud_soguk.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_grande.Checked == true)
                    {
                        toplam *= 1.25;
                        toplam *= Convert.ToDouble(nud_soguk.Value);
                        var eleman = "Grande Boy x " + cbx_Soguk.SelectedItem + " x " + nud_soguk.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_Venti.Checked == true)
                    {
                        toplam *= 1.75;
                        toplam *= Convert.ToDouble(nud_soguk.Value);
                        var eleman = "Venti Boy x " + cbx_Soguk.SelectedItem + " x " + nud_soguk.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_tall.Checked == true)
                    {
                        toplam *= 1;
                        toplam *= Convert.ToDouble(nud_soguk.Value);
                        var eleman = "Tall Boy x " + cbx_Soguk.SelectedItem + " x " + nud_soguk.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);

                    }
                    else
                    {
                        toplam *= 1;
                        toplam *= Convert.ToDouble(nud_soguk.Value);
                        var eleman = "Tall Boy x " + cbx_Soguk.SelectedItem + " x " + nud_soguk.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                }






            }

            #endregion

            #region sıcak icecekler

            if (cbx_Sıcak.SelectedValue != "" && nud_sıcak.Value != 0)
            {
                toplam += 7.5;

                if (cbx_1x.Checked == true && cbx_2x.Checked != true)
                {
                    toplam += 0.75;
                    if (rb_yagsiz.Checked == true)
                    {
                        toplam += 0.50;
                        toplam *= Convert.ToDouble(nud_sıcak.Value);
                        var eleman = "Yağsız süt x + 1x - " + cbx_Sıcak.SelectedItem + " x " + nud_sıcak.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_soya.Checked == true)
                    {
                        toplam += 0.50;
                        toplam *= Convert.ToDouble(nud_sıcak.Value);
                        var eleman = "Soya süt x + 1x -  " + cbx_Sıcak.SelectedItem + " x " + nud_sıcak.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_grande.Checked == true)
                    {
                        toplam *= 1.25;
                        toplam *= Convert.ToDouble(nud_sıcak.Value);
                        var eleman = "Grande Boy x + 1x -  " + cbx_Sıcak.SelectedItem + " x " + nud_sıcak.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_Venti.Checked == true)
                    {
                        toplam *= 1.75;
                        toplam *= Convert.ToDouble(nud_sıcak.Value);
                        var eleman = "Venti Boy x  + 1x - " + cbx_Sıcak.SelectedItem + " x " + nud_sıcak.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_tall.Checked == true)
                    {
                        toplam *= 1;
                        toplam *= Convert.ToDouble(nud_sıcak.Value);
                        var eleman = "Tall Boy x  + 1x - " + cbx_Sıcak.SelectedItem + " x " + nud_sıcak.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);

                    }
                    else
                    {
                        toplam *= 1;
                        toplam *= Convert.ToDouble(nud_sıcak.Value);
                        var eleman = "Tall Boy x  + 1x - " + cbx_Sıcak.SelectedItem + " x " + nud_sıcak.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                }
                else if (cbx_1x.Checked == true && cbx_2x.Checked == true)
                {
                    toplam += (0.75 * 3);

                    if (rb_yagsiz.Checked == true)
                    {
                        toplam += 0.50;
                        toplam *= Convert.ToDouble(nud_sıcak.Value);
                        var eleman = "Yağsız süt x + 3x - " + cbx_Sıcak.SelectedItem + " x " + nud_sıcak.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_soya.Checked == true)
                    {
                        toplam += 0.50;
                        toplam *= Convert.ToDouble(nud_sıcak.Value);
                        var eleman = "Soya süt x + 3x -  " + cbx_Sıcak.SelectedItem + " x " + nud_sıcak.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_grande.Checked == true)
                    {
                        toplam *= 1.25;
                        toplam *= Convert.ToDouble(nud_sıcak.Value);
                        var eleman = "Grande Boy x + 3x -  " + cbx_Sıcak.SelectedItem + " x " + nud_sıcak.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_Venti.Checked == true)
                    {
                        toplam *= 1.75;
                        toplam *= Convert.ToDouble(nud_sıcak.Value);
                        var eleman = "Venti Boy x  + 3x - " + cbx_Sıcak.SelectedItem + " x " + nud_sıcak.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_tall.Checked == true)
                    {
                        toplam *= 1;
                        toplam *= Convert.ToDouble(nud_sıcak.Value);
                        var eleman = "Tall Boy x  + 3x - " + cbx_Sıcak.SelectedItem + " x " + nud_sıcak.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);

                    }
                    else
                    {
                        toplam *= 1;
                        toplam *= Convert.ToDouble(nud_sıcak.Value);
                        var eleman = "Tall Boy x  + 3x - " + cbx_Sıcak.SelectedItem + " x " + nud_sıcak.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                }
                else if (cbx_1x.Checked != true && cbx_2x.Checked == true)
                {
                    toplam += (0.75 * 2);

                    if (rb_yagsiz.Checked == true)
                    {
                        toplam += 0.50;
                        toplam *= Convert.ToDouble(nud_sıcak.Value);
                        var eleman = "Yağsız süt x + 2x - " + cbx_Sıcak.SelectedItem + " x " + nud_sıcak.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_soya.Checked == true)
                    {
                        toplam += 0.50;
                        toplam *= Convert.ToDouble(nud_sıcak.Value);
                        var eleman = "Soya süt x + 2x -  " + cbx_Sıcak.SelectedItem + " x " + nud_sıcak.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_grande.Checked == true)
                    {
                        toplam *= 1.25;
                        toplam *= Convert.ToDouble(nud_sıcak.Value);
                        var eleman = "Grande Boy x + 2x -  " + cbx_Sıcak.SelectedItem + " x " + nud_sıcak.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_Venti.Checked == true)
                    {
                        toplam *= 1.75;
                        toplam *= Convert.ToDouble(nud_sıcak.Value);
                        var eleman = "Venti Boy x  + 2x - " + cbx_Sıcak.SelectedItem + " x " + nud_sıcak.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_tall.Checked == true)
                    {
                        toplam *= 1;
                        toplam *= Convert.ToDouble(nud_sıcak.Value);
                        var eleman = "Tall Boy x  + 2x - " + cbx_Sıcak.SelectedItem + " x " + nud_sıcak.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);

                    }
                    else
                    {
                        toplam *= 1;
                        toplam *= Convert.ToDouble(nud_sıcak.Value);
                        var eleman = "Tall Boy x  + 2x - " + cbx_Sıcak.SelectedItem + " x " + nud_sıcak.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }


                }

                else
                {
                    if (rb_yagsiz.Checked == true)
                    {
                        toplam += 0.50;
                        toplam *= Convert.ToDouble(nud_sıcak.Value);
                        var eleman = "Yağsız süt x " + cbx_Sıcak.SelectedItem + " x " + nud_sıcak.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_soya.Checked == true)
                    {
                        toplam += 0.50;
                        toplam *= Convert.ToDouble(nud_sıcak.Value);
                        var eleman = "Soya süt x " + cbx_Sıcak.SelectedItem + " x " + nud_sıcak.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_grande.Checked == true)
                    {
                        toplam *= 1.25;
                        toplam *= Convert.ToDouble(nud_sıcak.Value);
                        var eleman = "Grande Boy x " + cbx_Sıcak.SelectedItem + " x " + nud_sıcak.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_Venti.Checked == true)
                    {
                        toplam *= 1.75;
                        toplam *= Convert.ToDouble(nud_sıcak.Value);
                        var eleman = "Venti Boy x " + cbx_Sıcak.SelectedItem + " x " + nud_sıcak.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                    else if (rb_tall.Checked == true)
                    {
                        toplam *= 1;
                        toplam *= Convert.ToDouble(nud_sıcak.Value);
                        var eleman = "Tall Boy x " + cbx_Sıcak.SelectedItem + " x " + nud_sıcak.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);

                    }
                    else
                    {
                        toplam *= 1;
                        toplam *= Convert.ToDouble(nud_sıcak.Value);
                        var eleman = "Tall Boy x " + cbx_Sıcak.SelectedItem + " x " + nud_sıcak.Value + " Adet = " + toplam + " TL";

                        listBox1.Items.Add(eleman);
                    }
                }






            }

            #endregion


            toplam2 += toplam;

            lbl_SiparisTutar.Text = toplam2.ToString();

            cbx_Kahve.Text = "";
            cbx_Soguk.Text = "";
            cbx_Sıcak.Text = "";
            nud_kahve.Value = 0;
            nud_soguk.Value = 0;
            nud_sıcak.Value = 0;

            //richTextBox1.AppendText("\r\n"+Convert.ToString(toplam));

        }


        private void richTextBox1_TextChanged(object sender, EventArgs e)
        {

        }

        private void lbl_SiparisTutar_Click(object sender, EventArgs e)
        {

        }

        private void btn_Siparis_Ver_Click(object sender, EventArgs e)
        {

            DialogResult sonuc = MessageBox.Show("Siparişinizi onaylıyor musunuz?", "Bilgi", MessageBoxButtons.YesNo, MessageBoxIcon.Information);

            if (sonuc == DialogResult.Yes)
            {
                Baglanti b1 = new Baglanti();



                foreach (var item in listBox1.Items)
                {

                    SqlCommand insert = new SqlCommand("INSERT INTO Siparis (Cus_Name,Cus_Surname,Cus_Adress ,Itm_Name ,Itm_Price,Amount) VALUES (@p1,@p2,@p3,@p4,@p5,@p6)", b1.SQL());

                    insert.Parameters.AddWithValue("@p1", txt_ad.Text);
                    insert.Parameters.AddWithValue("@p2", txt_soyad.Text);
                    insert.Parameters.AddWithValue("@p3", rtbx_Adres.Text);
                    insert.Parameters.AddWithValue("@p4", tür.ToString());
                    insert.Parameters.AddWithValue("@p5", toplam.ToString());
                    insert.Parameters.AddWithValue("@p6", miktar.ToString());

                    insert.ExecuteNonQuery();

                    b1.SQL().Close();


                }


                MessageBox.Show("Siparişiniz eklenmiştir.", "Bilgi", MessageBoxButtons.OK, MessageBoxIcon.Information);

                toplam2 = 0;
                listBox1.Items.Clear();
                lbl_SiparisTutar.Text = "----------";
                txt_ad.Text = "";
                txt_soyad.Text = "";
                rtbx_Adres.Text = "";
            }
            else
            {
                //AnaMenü geridon = new AnaMenü();

                //geridon.Show();
            }
        }

        private void listBox1_MouseClick(object sender, MouseEventArgs e)
        {
        }

        private void btn_listboxsatırsil_Click(object sender, EventArgs e)
        {
            int secim = listBox1.SelectedIndex;
            if (secim != -1)
            {
                listBox1.Items.RemoveAt(secim);
            }
            else
            {
                MessageBox.Show("Seçim Yapın!");
            }
        }

        private void çıkışToolStripMenuItem_Click(object sender, EventArgs e)
        {
            Application.Exit();
        }

        private void anaMenüToolStripMenuItem_Click(object sender, EventArgs e)
        {
            //AnaMenü a1 = new AnaMenü();

            //this.Hide();
            //a1.Show();
        }

        private void siparişlerimToolStripMenuItem_Click(object sender, EventArgs e)
        {

            frm_Siparislerim s1 = new frm_Siparislerim();

            this.Close();
            s1.Show();



        }

        private void rtbx_Adres_TextChanged(object sender, EventArgs e)
        {

        }
    }
}
