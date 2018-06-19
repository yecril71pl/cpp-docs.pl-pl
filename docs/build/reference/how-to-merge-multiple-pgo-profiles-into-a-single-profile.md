---
title: 'Porady: scalanie wielu profili PGO w jeden profil | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- merging profiles
- profile-guided optimizations, merging profiles
ms.assetid: aab686b5-59dd-40d1-a04b-5064690f65a6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ca8fd6ef94af290d568f3186747c659b918c0fd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32372285"
---
# <a name="how-to-merge-multiple-pgo-profiles-into-a-single-profile"></a>Porady: scalanie wielu profili PGO w jeden profil

Optymalizacja sterowana profilem — (PGO) to doskonałe narzędzie do tworzenia zoptymalizowane pliki binarne, oparta na scenariuszu, który jest profilowane. Ale co zrobić, jeśli masz aplikację, która ma kilka ważnych, jeszcze różne scenariusze? Jak utworzyć jeden profil, który PGO można używać z kilku różnych scenariuszy W programie Visual Studio, Menedżer PGO [pgomgr.exe](pgomgr.md), wykonuje to zadanie.

Scalanie profili składnia jest następująca:

`pgomgr /merge[:num] [.pgc_files] .pgd_files`

gdzie `num` jest opcjonalny wagi do użycia dla plików PGC dodane przez tę operację scalania. Wagi są często używane, jeśli istnieje kilka scenariuszy, które są ważniejsze od innych użytkowników lub w przypadku scenariuszy, które mają być uruchamiane wiele razy.

> [!NOTE]
> Menedżer PGO nie działa z profilu starych danych. Aby scalić plik .pgc do pliku .pgd, plik .pgc musi zostać wygenerowany przez plik wykonywalny, który został utworzony przez tego samego wywołania łącza, który wygenerował plik .pgd.

## <a name="examples"></a>Przykłady

W tym przykładzie Menedżera PGO dodaje pgcFile.pgc do pgdFile.pgd sześć razy:

`pgomgr /merge:6 pgcFile.pgc pgdFile.pgd`

W tym przykładzie Menedżera PGO dodaje do pgdFile.pgd dwa razy dla każdego pliku .pgc pgcFile1.pgc i pgcFile2.pgc:

`pgomgr /merge:2 pgcFile1.pgc pgcFile2.pgc pgdFile.pgd`

Jeśli Menedżer PGO jest uruchamiany bez żadnych argumentów pliku .pgc, przeszukuje katalog lokalny dla wszystkich plików .pgc, które mają taką samą nazwę podstawową jak plik .pgd, a po niej znakiem wykrzyknika (!), a następnie co najmniej jeden znak dowolnego. Na przykład, jeśli katalog lokalny ma test.pgd pliki, test!1.pgc test2.pgc i test!hello.pgc i następujące polecenie jest uruchamiane z katalogu lokalnego, następnie **pgomgr** scala test!1.pgc i test!hello.pgc test.pgd.

`pgomgr /merge test.pgd`

## <a name="see-also"></a>Zobacz także

[Optymalizacje sterowane profilem](../../build/reference/profile-guided-optimizations.md)
