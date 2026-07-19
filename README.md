# Diagram UML — TravelKu

Diagram UML untuk aplikasi TravelKu Tiap file `.puml` sudah punya pasangan hasil render `.png` dengan **nama file (basename) yang identik** 

## Struktur folder

### `UseCaseDiagram/`
Actor dan fungsi bisnis sistem (kebutuhan bisnis tingkat tinggi).

| File | Isi |
|---|---|
| `use-case-diagram.puml` / `.png` | Actor Customer, 4 use case utama (Cari & Pesan Penerbangan, Cari & Pesan Hotel, Lihat Semua Pemesanan, Batalkan Reservasi), relasi `<<include>>` dan `<<extend>>` |

### `ActivityDiagram/`
Alur proses langkah-demi-langkah per use case, termasuk titik keputusan dan aktivitas paralel (fork/join).

| File | Isi |
|---|---|
| `activity-search-book-flight.puml` / `.png` | Alur cari & pesan penerbangan — decision validasi input/hasil kosong/pilihan, fork/join saat konfirmasi booking |
| `activity-search-book-hotel.puml` / `.png` | Alur cari & pesan hotel — struktur sama seperti penerbangan |
| `activity-cancel-reservation.puml` / `.png` | Alur pembatalan reservasi — decision tipe reservasi (flight/hotel) |
| `activity-view-reservations.puml` / `.png` | Alur lihat semua pemesanan — decision daftar kosong + loop tampilkan reservasi |

### `ClassDiagram/`
Struktur statis sistem: class, atribut/metode, dan relasi (asosiasi, multiplisitas, generalisasi/pewarisan, realization, composition, dependency).

| File | Isi |
|---|---|
| `class-diagram.puml` / `.png` | Seluruh class domain: `TravelApp`, `Flight`, `Hotel`, `Reservation` (abstract) → `FlightReservation`/`HotelReservation`, `Bookable` (interface), `ReservationNotFoundException`, `ConfirmationNumberGenerator` |

### `SequenceDiagram/`
Interaksi antar objek (lifeline + pesan + activation bar) untuk skenario transaksi utama.

| File | Isi |
|---|---|
| `sequence-book-flight.puml` / `.png` | Skenario pelanggan memesan penerbangan — dari input kriteria sampai kotak konfirmasi |
| `sequence-book-hotel.puml` / `.png` | Skenario pelanggan memesan hotel — struktur sama seperti penerbangan |
| `sequence-cancel-reservation.puml` / `.png` | Skenario pembatalan reservasi — `alt` sukses vs `ReservationNotFoundException` |



## Cara render ulang

pastikan plantuml sudah ter install

```bash
plantuml UseCaseDiagram/*.puml
plantuml ActivityDiagram/*.puml
plantuml ClassDiagram/*.puml
plantuml SequenceDiagram/*.puml
```

Atau semua sekaligus dari folder `uml/`:

```bash
plantuml **/*.puml
```

Output `.png` otomatis dinamai sama dengan basename `.puml`-nya (directive `@startuml` di tiap file  dibiarkan tanpa nama custom)
