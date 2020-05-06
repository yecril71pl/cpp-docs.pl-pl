---
title: 'Porady: scalanie wielu profili PGO w jeden profil'
ms.date: 03/14/2018
helpviewer_keywords:
- merging profiles
- profile-guided optimizations, merging profiles
ms.assetid: aab686b5-59dd-40d1-a04b-5064690f65a6
ms.openlocfilehash: 451c0f30a271f5dce3974e172766da4a23340b93
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188876"
---
# <a name="how-to-merge-multiple-pgo-profiles-into-a-single-profile"></a>Porady: scalanie wielu profili PGO w jeden profil

Optymalizacja oparta na profilach (PGO) to doskonałe narzędzie do tworzenia zoptymalizowanych plików binarnych na podstawie scenariusza, który jest profilowany. Ale co zrobić, jeśli masz aplikację, która ma kilka ważnych, a jeszcze różne scenariusze? Jak utworzyć pojedynczy profil, który PGO może być używany z kilku różnych scenariuszy? W programie Visual Studio, PGO Manager, [Pgomgr. exe](pgomgr.md), robi to zadanie.

Składnia scalania profilów jest następująca:

`pgomgr /merge[:num] [.pgc_files] .pgd_files`

gdzie `num` jest opcjonalną wagą do użycia dla plików. PGC dodanych przez ten scalanie. Wagi są często używane, jeśli istnieją pewne scenariusze, które są ważniejsze niż inne, lub jeśli istnieją scenariusze, które mają być uruchamiane wiele razy.

> [!NOTE]
> Program PGO Manager nie działa w przypadku starych danych profilu. Aby scalić plik. PGC do pliku. pgd, plik. PGC musi być wygenerowany przez plik wykonywalny, który został utworzony przez to samo wywołanie linku, które wygenerowało plik. pgd.

## <a name="examples"></a>Przykłady

W tym przykładzie Menedżer PGO dodaje pgcFile. PGC do pgdFile. PGD sześć razy:

`pgomgr /merge:6 pgcFile.pgc pgdFile.pgd`

W tym przykładzie PGO Manager dodaje pgcFile1. PGC i pgcFile2. PGC do pgdFile. pgd, dwa razy dla każdego pliku. PGC:

`pgomgr /merge:2 pgcFile1.pgc pgcFile2.pgc pgdFile.pgd`

Jeśli Menedżer PGO jest uruchamiany bez żadnych argumentów pliku. PGC, przeszukuje katalog lokalny dla wszystkich plików. PGC o takiej samej nazwie bazowej jak plik. pgd, po którym następuje znak wykrzyknika (!), a następnie co najmniej jeden dowolny znak. Na przykład, jeśli katalog lokalny zawiera pliki test. pgd, test! 1. PGC, TEST2. PGC i test! Hello. PGC, a poniższe polecenie jest uruchamiane z katalogu lokalnego, a następnie **pgomgr** Scala test! 1. PGC i test! Hello. pgc.

`pgomgr /merge test.pgd`

## <a name="see-also"></a>Zobacz też

[Optymalizacje sterowane profilem](profile-guided-optimizations.md)
