# 2280601517_NguyenKhoa_baitaptuan2
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;


namespace Baitaptuan2
{
    internal class Program
    {
        public class SinhVien
        {
            public int ID { get; set; }
            public string Name { get; set; }
            public int Age { get; set; }

            public SinhVien(int ID, string Name, int Age)
            {
                this.ID = ID;
                this.Name = Name;
                this.Age = Age;
            }

            public override string ToString()
            {
                return ("ID: " + this.ID + " Name: " + this.Name + " Age: " + this.Age);
            }
        }

        static void Main(string[] args)
        {
            Console.OutputEncoding = Encoding.UTF8;
            // Initialize the list of students
            var sinhvien = new List<SinhVien>
            {
                new SinhVien(1, "Khoa", 16),
                new SinhVien(2, "Duyen", 18),
                new SinhVien(3, "My", 19),
                new SinhVien(4, "Hung", 17),
                new SinhVien(5, "Anh", 20)
            };
            Console.WriteLine("Danh sách học sinh:\n");
            foreach (var sinhVien in sinhvien)
            {
                Console.WriteLine(sinhVien);
            }
            Console.WriteLine("\nDanh sach hoc sinh co tuoi tu 15 den 18 la:\n ");
            var ketqua = from sv in sinhvien
                         where sv.Age >= 15 && sv.Age <= 18
                         select sv;
            foreach (var sinhviens in ketqua)
            {
                Console.WriteLine(sinhviens.ToString());
            }
            Console.WriteLine("\nhoc sinh co ten bat dau bang chu A la:\n ");
            var ketqua2 = from sv in sinhvien
                          where sv.Name.StartsWith(" A ")
                          select sv;
            foreach (var sinhviens1 in ketqua2)
            {
                Console.WriteLine(sinhviens1.ToString());
            }
            Console.Write("\nTong tuoi cua tat ca hoc sinh trong danh sach = : ");
            var tongtuoi = (from tong in sinhvien
                            select tong.Age).Sum();
            {
                Console.WriteLine(tongtuoi);
            }
            Console.Write("\nHoc sinh co tuoi cao nhat la:\n ");
            var tuoi = (from tuoi1 in sinhvien
                        orderby tuoi1.Age descending
                        select tuoi1).FirstOrDefault();
            Console.WriteLine("\nID: " + tuoi.ID + "  Name " + tuoi.Name + "  Age " + tuoi.Age);
            Console.WriteLine("\ndanh sach sap xep tuoi tang dan:\n ");
            var sapxep = from tuoi2 in sinhvien.OrderByDescending(x => x.Age)
                         orderby tuoi2.Age ascending
                         select tuoi2;
            foreach (var sv2 in sapxep)
            {
                Console.WriteLine(sv2);
            }
            Console.ReadLine();
        }
    }
}
