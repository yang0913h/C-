C#
how to transfer large-size(.tiff) image to (.png) in C#
image-size : (30000px*20000px) 2.2MB
i try this,but bitmap limit (15722*15722);
            foreach (string fname in System.IO.Directory.GetFileSystemEntries(savePath + "img_data/", "*.tif"))  //fname 該資料夾下的檔案絕對路徑
            {
                string main_filename = Path.GetFileNameWithoutExtension(fname);  // 抓主檔名   

                if (!File.Exists(savePath + "img_data/" + main_filename + ".png"))
                {
                    Image image = Image.FromFile(fname);
                    //開啟圖片
                    try
                    {
                        Bitmap bitmap = new Bitmap(image, image.Width, image.Height);
                        image = bitmap;

                        image.Save(savePath + "img_data/" + main_filename + ".png", ImageFormat.Png);

                        bitmap.Dispose();
                        image.Dispose();                //記憶體釋放
                    }
                    catch (Exception e)
                    {
                        System.Diagnostics.Debug.WriteLine(main_filename);
                        str.WriteLine(main_filename);
                    }
                    System.GC.Collect();
                    System.GC.WaitForPendingFinalizers();
                    System.GC.Collect();
                }
            }
            
thx for your read.
