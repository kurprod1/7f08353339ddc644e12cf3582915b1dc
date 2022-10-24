# Konsep SSL pada Android

Created: June 22, 2022 1:17 PM

Sekarang secara teknis dikenal sebagai Transport Layer Security (TLS). Biasanya untuk keamanan pada pengiriman data antara aplikasi ke server backend memerlukan teknologi enkripsi sehingga TLS diperlukan.

Dalam skenario penggunaan SSL umum, server dikonfigurasi dengan sertifikat yang berisi kunci publik serta kunci pribadi yang cocok. Sebagai bagian dari handshake antara klien dan server SSL, server membuktikan kepemilikan kunci pribadi dengan menandatangani sertifikat dengan kriptografi kunci publik.

[https://lh5.googleusercontent.com/ip-KacrWS83MFJXPTWuSmbd_-5YjD5h4ns0mGqbufyuIYhjXGDabF5ii50-RC6__6l81wG0xz4XyC0jOjB3EpiFaYBpI6as_yJPOVRkdYVNSFs9-adI6I82JszOqCaHvWk6lrKSdpHrIHy7b6ePFJWws0Ww](https://lh5.googleusercontent.com/ip-KacrWS83MFJXPTWuSmbd_-5YjD5h4ns0mGqbufyuIYhjXGDabF5ii50-RC6__6l81wG0xz4XyC0jOjB3EpiFaYBpI6as_yJPOVRkdYVNSFs9-adI6I82JszOqCaHvWk6lrKSdpHrIHy7b6ePFJWws0Ww)

Namun, siapa pun dapat menghasilkan sertifikat dan kunci pribadi sendiri, sehingga handshake yang sederhana tidak membuktikan apapun tentang server selain bahwa server mengetahui kunci pribadi yang cocok dengan kunci publik sertifikat.

[https://lh5.googleusercontent.com/CUK7_5eWSIJls71QTbjNllwgIre1NrkxZMAXCEAPYMHk51DhFFb-RNV63tddzmB-U2QSxFuoeXDy1u90udQlwIaQU_w8I7nuUJKyB1y5Xq7tA0qHMvLizNseSvTbSgX5am54B_b7JIKmNCjzUCpEj6K3ZE4](https://lh5.googleusercontent.com/CUK7_5eWSIJls71QTbjNllwgIre1NrkxZMAXCEAPYMHk51DhFFb-RNV63tddzmB-U2QSxFuoeXDy1u90udQlwIaQU_w8I7nuUJKyB1y5Xq7tA0qHMvLizNseSvTbSgX5am54B_b7JIKmNCjzUCpEj6K3ZE4)

Salah satu cara untuk memecahkan masalah ini adalah meminta klien memiliki kumpulan satu atau beberapa sertifikat yang dipercaya. Jika sertifikat tidak ada dalam kumpulan tersebut, server tidak bisa dipercaya.

[https://lh3.googleusercontent.com/hoBcChF7NEWtqKrezest-Gm1RAroi7w9Aej0nGtCtvXO4-6r-ON_vXrjiqa0h-ZOjMKEap_eQuaGBoTM4A57rJh-UetsYCOtPDrgn6qP0k_Zl6RdXKmTGpeCr3vh3aiMcoi5Ad6B21QjHV5iIBB0av1RN-s](https://lh3.googleusercontent.com/hoBcChF7NEWtqKrezest-Gm1RAroi7w9Aej0nGtCtvXO4-6r-ON_vXrjiqa0h-ZOjMKEap_eQuaGBoTM4A57rJh-UetsYCOtPDrgn6qP0k_Zl6RdXKmTGpeCr3vh3aiMcoi5Ad6B21QjHV5iIBB0av1RN-s)

Jika teman-teman menemukan pesan peringatan di dibawah ini artinya sertifikat tidak dipercaya dikarenakan saat ditinjau dengan Root CA dianggap tidak terpercaya. Sedangkan intermediate root CA merupakan organisasi yang mengeluarkan sertifikat.

[https://lh6.googleusercontent.com/S_uXV1cH-gJHUShHaXo9K-JyaJeH11MwW_NJxHjteImJLvqy3eDaj9_VCe267H52A1MUo2_IeiJnHPGGUYibQtDuShZE9lVM3MRH9nkX8bhryCPGPMz4diaP441JNPpfj17jssHymLwaIjHApb0qUF6SxWA](https://lh6.googleusercontent.com/S_uXV1cH-gJHUShHaXo9K-JyaJeH11MwW_NJxHjteImJLvqy3eDaj9_VCe267H52A1MUo2_IeiJnHPGGUYibQtDuShZE9lVM3MRH9nkX8bhryCPGPMz4diaP441JNPpfj17jssHymLwaIjHApb0qUF6SxWA)

Dari gambar diatas bisa kita tahu bahwa sertifikat yang tercantum adalah palsu. Pemalsuan ini dilakukan secara otomatis dengan Burp. Bandingkan dengan sertifikat cilsy.id yang asli sebagai berikut :

[https://lh5.googleusercontent.com/bClJ7MVuyGdvN0zdxTNKowRLSEEVVsqNm1O8I7p348vFxvTDisrYgEIlCvbYXR6A1baOmdwhQG1dYJwMmMHBpybxiOu4hpYBN1dHoeRjOPAlQC8DwkIlUiBnM25-EdTyO-Wcinr11YZjaZLvm47HYp980OU](https://lh5.googleusercontent.com/bClJ7MVuyGdvN0zdxTNKowRLSEEVVsqNm1O8I7p348vFxvTDisrYgEIlCvbYXR6A1baOmdwhQG1dYJwMmMHBpybxiOu4hpYBN1dHoeRjOPAlQC8DwkIlUiBnM25-EdTyO-Wcinr11YZjaZLvm47HYp980OU)

Nah maka dari itu pemeriksaan lanjutan mengenai kepercayaan sertifikat harus dilakukan dengan root CA. Teman-teman bisa mengklik **Details** pada popup window diatas maka kita akan bisa melihat sertifikat cloudflare yang dipake cilsy.id di verifikasi oleh perusahaan mana.

[https://lh6.googleusercontent.com/3WMj35Z-PvhAt4Y5OxZf94i5MHH-DdKkqDt02jySlCdG8vHbEJbgkV5ZA5GfszI5Wab87d8uNiDft_vhPvsDVClixLUS1osu0OFT15noLck4qhtJryp7-0BlOClk6ZOrKpXZE1FHl0tf9IxE1fY7YvNdLxE](https://lh6.googleusercontent.com/3WMj35Z-PvhAt4Y5OxZf94i5MHH-DdKkqDt02jySlCdG8vHbEJbgkV5ZA5GfszI5Wab87d8uNiDft_vhPvsDVClixLUS1osu0OFT15noLck4qhtJryp7-0BlOClk6ZOrKpXZE1FHl0tf9IxE1fY7YvNdLxE)

Nah pada perangkat android semua sertifikat tersimpan pada menu setting > security & location > encryption & credentials > trusted credentials.

[https://lh5.googleusercontent.com/3xnK2IpLhhHI80e-Wj4ul34a9COe4BuV-8YL6wuBcoHuvbNoUxd4e-4BXFo4pIDeM8bbpFtzH2rJ3MF83v6RD92bz5uvAYkZkng5-nClj9mWyXJbySQ19GjsjdgEiFfMo0G-cOCzUu41uaX6jAMAWvkBumc](https://lh5.googleusercontent.com/3xnK2IpLhhHI80e-Wj4ul34a9COe4BuV-8YL6wuBcoHuvbNoUxd4e-4BXFo4pIDeM8bbpFtzH2rJ3MF83v6RD92bz5uvAYkZkng5-nClj9mWyXJbySQ19GjsjdgEiFfMo0G-cOCzUu41uaX6jAMAWvkBumc)