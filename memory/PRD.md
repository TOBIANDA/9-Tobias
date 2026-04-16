# Siklus - Book Exchange Community (Laravel)

## Original Problem Statement
User meminta untuk menyelesaikan semua halaman yang belum dikerjakan dan memperbaiki bug yang masih ada dalam web berbasis Laravel.

## Architecture
- **Framework**: Laravel 12 (PHP 8.2)
- **Server**: Nginx + PHP-FPM
- **CSS**: Custom CSS (public/css/app.css)
- **Database**: Belum diintegrasikan (data hardcoded di routes/web.php)
- **Template**: Blade templates
- **Port**: Nginx listens on port 3000

## User Personas
- Mahasiswa yang meminjam buku antar sesama
- Peminjam (Borrower) dan Pemilik buku (Lender)

## Core Requirements
- Homepage dengan popular & recommended books
- Detail buku dengan deskripsi, review, dan lenders
- Sistem pesan antar user
- Halaman borrow & lent books
- Profil user dengan edit profile
- Pencarian buku
- Form tambah buku baru

## What's Been Implemented (April 16, 2026)

### Halaman yang Diselesaikan:
1. **Search Page** (`/search`) - Pencarian buku berfungsi dengan filter title, author, genre
2. **Add Book Form** (`/borrow/add`) - Form lengkap: cover, title, author, genre, language, pages, description, condition, location
3. **Profile Edit** (`/profile/edit`) - Form edit: nama, occupation, bio, change photo
4. **Lent Page** (`/lent`) - Dilengkapi: On Loan, Pending Requests (Accept/Reject), Finished Loans

### Bug Fixes:
1. Fixed search route yang hanya return string -> sekarang render view dengan data
2. Fixed borrow/add route yang hanya return string -> sekarang render form lengkap
3. Fixed missing routes: `profile.edit`, `profile.update`, `profile.photo`, `messages.send`, `borrow.submit`, `borrow.store`
4. Fixed Lent page yang tidak menampilkan Pending Requests dan Finished Loans
5. Fixed Borrow page - menambahkan data untuk semua 3 status (onread, appeal, finish)
6. Fixed asset URLs (dari internal cluster hostname ke relative paths)
7. Fixed Vite dependency (removed @vite directive, gunakan static CSS)
8. Fixed URL generation (forceScheme + forceRootUrl)

### Infrastructure:
- Installed PHP 8.2 + PHP-FPM
- Installed MariaDB
- Configured Nginx to serve Laravel on port 3000
- Set ASSET_URL=/ for relative asset paths
- Configured URL::forceScheme('https') in AppServiceProvider

## Prioritized Backlog
### P0 (Completed)
- [x] All pages render correctly
- [x] Search functionality
- [x] Add Book form
- [x] Profile Edit page
- [x] Lent page complete sections
- [x] All route definitions

### P1 (Next Phase - Backend Integration)
- [ ] Database models (User, Book, BorrowRequest, Message, Notification)
- [ ] Authentication system (login/register)
- [ ] Real CRUD operations
- [ ] File upload functionality

### P2 (Enhancements)
- [ ] Real-time messaging (WebSocket)
- [ ] Email notifications
- [ ] Rating system
- [ ] Book recommendation algorithm
