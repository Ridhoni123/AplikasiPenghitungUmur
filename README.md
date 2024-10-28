import tkinter as tk
from tkinter import messagebox

class AplikasiPenjumlahan:
    def __init__(self, root):
        self.root = root
        self.root.title("Aplikasi Pertambahan Dua Angka")

        # Membuat label dan entry untuk angka pertama
        self.label_angka1 = tk.Label(root, text="Angka 1")
        self.label_angka1.grid(row=0, column=0)
        self.entry_angka1 = tk.Entry(root)
        self.entry_angka1.grid(row=0, column=1)

        # Membuat label dan entry untuk angka kedua
        self.label_angka2 = tk.Label(root, text="Angka 2")
        self.label_angka2.grid(row=1, column=0)
        self.entry_angka2 = tk.Entry(root)
        self.entry_angka2.grid(row=1, column=1)

        # Membuat label hasil
        self.label_hasil = tk.Label(root, text="Hasil")
        self.label_hasil.grid(row=2, column=0)
        self.entry_hasil = tk.Entry(root, state="readonly")
        self.entry_hasil.grid(row=2, column=1)

        # Membuat tombol tambah
        self.tombol_tambah = tk.Button(root, text="Tambah", command=self.tambah)
        self.tombol_tambah.grid(row=3, column=0)

        # Membuat tombol hapus
        self.tombol_hapus = tk.Button(root, text="Hapus", command=self.hapus)
        self.tombol_hapus.grid(row=3, column=1)

        # Membuat tombol keluar
        self.tombol_keluar = tk.Button(root, text="Keluar", command=root.quit)
        self.tombol_keluar.grid(row=3, column=2)

    def tambah(self):
        try:
            angka1 = float(self.entry_angka1.get())
            angka2 = float(self.entry_angka2.get())
            hasil = angka1 + angka2
            self.entry_hasil.config(state="normal")
            self.entry_hasil.delete(0, tk.END)
            self.entry_hasil.insert(0, str(hasil))
            self.entry_hasil.config(state="readonly")
        except ValueError:
            messagebox.showerror("Input Error", "Masukkan angka yang valid")

    def hapus(self):
        self.entry_angka1.delete(0, tk.END)
        self.entry_angka2.delete(0, tk.END)
        self.entry_hasil.config(state="normal")
        self.entry_hasil.delete(0, tk.END)
        self.entry_hasil.config(state="readonly")
        self.entry_angka1.focus()

# Main program
if __name__ == "__main__":
    root = tk.Tk()
    app = AplikasiPenjumlahan(root)
    root.mainloop()
