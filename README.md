# winform-C-_-MouseWheel-
//构造方法里面提添加鼠标wheel事件
思路:
	主界面添加一个panel，将用户控件放在此panel里面，在panel
或者主界面里面添加MouseWheel事件，根据鼠标滑轮事件重绘窗体的位置，就能实现窗体的滑动，以下代码供参考




#region 构造
        public TodayNews()
        {
            InitializeComponent();
            this.MouseWheel += new MouseEventHandler(this.purl_MouseWheel);//添加事件
        }
#endregion


//根据数据重绘窗体位置，记得要开双重缓冲，否则会出现严重闪烁


#region 窗体滚动
        public void purl_MouseWheel(object sender, System.Windows.Forms.MouseEventArgs e)
        {


            if (e.Delta > 0)//判断wheel的返回的值，正为向上滑，负为向下
            {
                if (this.uRl1.Location.Y+20  >0)//这里是判断用户控件在panel的位置，为防止将控件滑出了panel
                    return;

                this.uRl1.Location = new Point(this.uRl1.Location.X, this.uRl1.Location.Y + 20);//更新窗体位置
            }
            else
            {
                if (this.uRl1.Location.Y + this.uRl1.Height-20 < 600)
                    return;//这里是判断用户控件在panel的位置，为防止将控件滑出了panel

                this.uRl1.Location = new Point(this.uRl1.Location.X, this.uRl1.Location.Y - 20);//更新窗体位置
            }
        }
#endregion


