---
layout: post
title:  "Apa itu Lazy Loading? Pengertian Lazy Loading"
date:   2015-08-31 19:19:00 +0700
categories: technology
permalink: apa-itu-lazy-loading-pengertian-lazy-loading/
---

Lazy loading adalah sebuah konsep dimana kita menunda pemanggilan (load) sebuah objek sampai di saat kita memang membutuhkannya. Dengan kata lain lazy loading menunda pemanggilan objek ketika objek masih belum dibutuhkan.

![Lazy Cat on Computer](/images/lazy-cat.jpg)

Sebagai contoh seandainya kita memiliki class Customer dan Costumer memiliki banyak objek Order di dalamnya. Perhatikan bagian konstruktor pada class Costumer, dimana ketika objek Costumer dibuat, aplikasi juga membuat objek Order pada waktu yang sama. Sehingga meskipun kita tidak memerlukan objek Order, objek ini tetap dibuat. Proses seperti ini, berlawanan dengan *Lazy Loading*, disebut dengan *Eager Loading*.

```
public class Customer
{
  private List<Order> _Orders= null;
  …
  …
  public Customer()
  {
        _CustomerName = "Shiv";
        _Orders = LoadOrders(); // Loads the order object even though //not needed
  }

  private List<Order> LoadOrders()
  {
        List<Order> temp = new List<Order>();
        Order o = new Order();
        o.OrderNumber = "ord1001";
        temp.Add(o);
        o = new Order();
        o.OrderNumber = "ord1002";
        temp.Add(o);
        return temp;
  }
}
```

## Implementasi Lazy Loading

Untuk mengimplementasikan Lazy Loading ke dalam kode diatas, kita dapat melakukan perubahan berikut:

1. Hapus load objek Order pada konstruktor
2. Pada pengambilan properti order pada objek yang telah dibuat, lakukan pengecekan: jika property order masih kosong, maka lakukan pengambilan data.

```
public class Customer
{
    private List<Order> _Orders= null;
    …
    …
    public Customer()
    {
        _CustomerName = "Shiv";
    }
    public List<Order> Orders
    {
      get
        {
            if (_Orders == null)
            {
                _Orders = LoadOrders();
            }
            return _Orders;
        }
    }
```

## Keuntungan dan kerugian menggunakan lazy loading

Keuntungan menggunakan lazy loading yaitu:

1. Meminimilasi waktu start up aplikasi
2. Aplikasi membutuhkan memory yang lebih sedikit karena objek hanya di load ketika dibutuhkan.
3. Pemanggilan Query database yang tidak diperlukan dapat dihindari.

Kerugian menggunakan lazy loading hanyalah kode program jadi sedikit lebih rumit, dan membutuhkan sedikit proses ketika pengecekan property, tapi keuntungan yang diberikan jauh lebih besar daripada kerugiannya.

Semoga bermanfaat
