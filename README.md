# code+

Kumpulan **system prompt** untuk AI coding agent. Proyek ini hanya berisi file prompt yang bisa dipasang ke agent apa pun (chatbot, IDE assistant, CLI agent) untuk menghasilkan perilaku layaknya senior software engineer.

## Isi Repo

| File | Deskripsi |
| --- | --- |
| `SYSTEM_PROMPT.md` | System prompt utama: kerangka berpikir, mode kerja, dan struktur respons wajib. |
| `+SKILL_EXPLORER.md` | Varian lanjutan yang menambahkan **Skill Discovery & Capability Expansion** — agent dapat mengevaluasi dan merekomendasikan skill eksternal (dengan persetujuan user). |

## Tujuan

Kedua prompt mengubah AI dari "penjawab cepat" menjadi **senior engineer dengan pengalaman luas** yang mengutamakan solusi benar, andal, dan maintainable — bukan jawaban cepat.

Prinsip intinya:

- **Think before answering** — pahami masalah, konteks, dan asumsi sebelum menulis kode.
- **Root cause, bukan symptom** — pakai Five Whys, fault isolation, dan dependency analysis.
- **Correctness over cleverness** — kode harus production-ready, bukan sekadar contoh.
- **Honest about uncertainty** — menyatakan asumsi dan level keyakinan secara eksplisit.

## Mode Kerja yang Didefinisikan

1. **Problem Analysis Framework** — definisi masalah, konteks, root cause, desain solusi, implementasi.
2. **Planning Requirement** — buat rencana (objective, approach, steps, risks, validation) sebelum eksekusi tugas besar.
3. **Coding Behavior** — kode production-ready dengan error handling, validasi, dan trade-off yang jelas.
4. **Debugging Mode** — protokol 5 langkah: restate masalah, kategorikan penyebab, ranking hipotesis, uji verifikasi, perbaikan minimal.
5. **Code Review Mode** — analisis 7 aspek (fungsionalitas, logika, arsitektur, performa, keamanan, maintainability, testing).
6. **Document Analysis Mode** — pembacaan dokumen teknis berlapis (7 layer).
7. **Architecture Thinking** — berpikir dalam sistem: input, proses, output, failure mode, recovery.
8. **Decision Making** — bandingkan opsi (kelebihan/kekurangan/use case) lalu rekomendasikan satu.

## Skill Discovery (`+SKILL_EXPLORER.md`)

Varian ini menambahkan alur khusus untuk memperluas kemampuan agent:

1. **Evaluasi capability gap** — apakah kemampuan bawaan cukup untuk menyelesaikan tugas secara optimal?
2. **Skill Evaluation Process** — analisis capability gap, tujuan skill, ekspektasi peningkatan (akurasi, kecepatan, kualitas, reliabilitas), dan risiko.
3. **User Approval wajib** — agent **tidak boleh** menginstal skill secara otomatis; harus menawarkan opsi (A/B/C/D) dan menunggu persetujuan.
4. **Instalasi & validasi** — setelah disetujui, install, validasi hasil, lalu susun execution plan per skill.
5. **Quality Control Loop** — self-review sebelum respons final.

Contoh perintah instalasi yang dirujuk:

```bash
npx skill install <skill-name>
```

## Struktur Respons Wajib

Untuk masalah teknis kompleks, prompt memaksa urutan berikut:

1. Understanding the Problem
2. Key Assumptions
3. Analysis
4. Proposed Solution / Recommended Approach
5. Implementation
6. Validation
7. Risks and Improvements

## Cara Pakai

**Chatbot / LLM playground**

Salin seluruh isi `SYSTEM_PROMPT.md` (atau `+SKILL_EXPLORER.md` bila agent perlu kemampuan discover & install skill) ke kolom *system instruction* / *custom instructions*.

**IDE assistant / CLI agent (Claude, Cursor, Kilo, dll.)**

Tempatkan sebagai file aturan tingkat proyek:

```text
CLAUDE.md        # [CC]
AGENTS.md        # agent generik
.kilo/           # Kilo
```

atau referensikan langsung:

```text
Baca SYSTEM_PROMPT.md dan patuhi seluruh aturannya untuk sesi ini.
```

## Perbandingan Singkat

| Aspek | `SYSTEM_PROMPT.md` | `+SKILL_EXPLORER.md` |
| --- | --- | --- |
| Fokus | Reasoning & engineering behavior | Reasoning + skill discovery |
| Planning eksplisit | Implisit | Wajib untuk tugas menengah/besar |
| Skill installation | — | Ya, dengan approval user |
| Cocok untuk | Chatbot/agent umum | Agent yang bisa extend capability |

## Prinsip Level Keyakinan

Prompt mendorong AI menyatakan tingkat keyakinan secara eksplisit:

- **High confidence** — berdasarkan bukti jelas.
- **Medium confidence** — berdasarkan pola umum.
- **Low confidence** — perlu validasi.

## Aturan Akhir

> Tujuan bukan menjawab cepat, tetapi menghasilkan jawaban yang dipercaya senior engineer sebelum deploy ke produksi.
> Think deeply. Plan first. Verify assumptions. Solve root causes. Deliver robust solutions.

## Lisensi

Bebas digunakan dan dimodifikasi.
