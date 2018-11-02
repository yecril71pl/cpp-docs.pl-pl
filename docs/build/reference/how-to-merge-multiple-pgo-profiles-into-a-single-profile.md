---
title: 'Porady: scalanie wielu profili PGO w jeden profil'
ms.date: 03/14/2018
helpviewer_keywords:
- merging profiles
- profile-guided optimizations, merging profiles
ms.assetid: aab686b5-59dd-40d1-a04b-5064690f65a6
ms.openlocfilehash: 04730524fa756b0c6f1e505f3610609bdec6262a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476547"
---
# <a name="how-to-merge-multiple-pgo-profiles-into-a-single-profile"></a>Porady: scalanie wielu profili PGO w jeden profil

Profilowana Optymalizacja (PGO) jest doskonałym narzędziem do tworzenia zoptymalizowanych plików binarnych, oparta na scenariuszu, która jest profilowana. Ale co zrobić, jeśli masz aplikację, która ma kilka ważnych scenariuszy jeszcze distinct? Jak utworzyć jeden profil, który można użyć funkcji optymalizacji PGO z kilku różnych scenariuszy W programie Visual Studio, Menedżer PGO [pgomgr.exe](pgomgr.md), wykonuje to zadanie.

Scalanie profili składnia jest następująca:

`pgomgr /merge[:num] [.pgc_files] .pgd_files`

gdzie `num` jest opcjonalny waga do użycia dla plików PGC dodane przez takiego połączenia. Wagi są często używane, jeśli istnieją pewne scenariusze, które są ważniejsze niż inne, lub jeśli istnieją scenariusze, które mają być uruchamiane wielokrotnie.

> [!NOTE]
> Menedżer PGO działa z użyciem danych profilu starych. Aby scalić plik .pgc do pliku .pgd, plik .pgc musi zostać wygenerowany przez plik wykonywalny, który został utworzony przez tego samego wywołania łącza, który wygenerował plik .pgd.

## <a name="examples"></a>Przykłady

W tym przykładzie Menedżer PGO dodaje pgcFile.pgc do pgdFile.pgd sześć razy:

`pgomgr /merge:6 pgcFile.pgc pgdFile.pgd`

W tym przykładzie Menedżer PGO dodaje pgcFile1.pgc i pgcFile2.pgc do pgdFile.pgd dwa razy dla każdego pliku .pgc:

`pgomgr /merge:2 pgcFile1.pgc pgcFile2.pgc pgdFile.pgd`

Jeśli Menedżer PGO zostanie uruchomione bez żadnych argumentów pliku .pgc, przeszukuje katalog lokalny dla wszystkich plików .pgc, które mają taką samą nazwę jak plik .pgd następuje znak wykrzyknika (!), a następnie co najmniej jeden znak dowolnego. Na przykład, jeśli katalog lokalny ma test.pgd pliki, test!1.pgc, test2.pgc i test!hello.pgc, a polecenie jest uruchamiany z katalogu lokalnego, następnie **pgomgr** scala test.pgd test!1.pgc i test!hello.pgc.

`pgomgr /merge test.pgd`

## <a name="see-also"></a>Zobacz także

[Optymalizacje sterowane profilem](../../build/reference/profile-guided-optimizations.md)
