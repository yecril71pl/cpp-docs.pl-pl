---
title: 'Porady: scalanie wielu profili PGO w jeden profil | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- merging profiles
- profile-guided optimizations, merging profiles
ms.assetid: aab686b5-59dd-40d1-a04b-5064690f65a6
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: dcd10c25e4512683b840bd2feeee287995ab8776
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-merge-multiple-pgo-profiles-into-a-single-profile"></a>Porady: scalanie wielu profili PGO w jeden profil
Optymalizacja sterowana profilem — (PGO) to doskonałe narzędzie do tworzenia zoptymalizowane pliki binarne, oparta na scenariuszu, który jest profilowane. Ale co zrobić, jeśli masz aplikację, która ma kilka ważnych, jeszcze różne scenariusze; jak utworzyć jeden profil, który PGO można używać z kilku różnych scenariuszy W programie Visual Studio Menedżer PGO, Pgomgr.exe, wykonuje to zadanie możesz.  
  
 Scalanie profili składnia jest następująca:  
  
```  
pgomgr /merge[:num] [.pgc_files] .pgd_files  
```  
  
 gdzie `num` jest opcjonalny wagi, który jest używany przez tę operację scalania. Wagi są często używane, jeśli istnieje kilka scenariuszy, które są ważniejsze od innych użytkowników lub w przypadku scenariuszy, które mają być uruchamiane wiele razy.  
  
> [!NOTE]
>  Menedżer PGO nie będzie działać z profilu starych danych. Aby scalić plik .pgc do pliku .pgd, plik .pgc musi zostać wygenerowany przez plik wykonywalny, który został utworzony przez tego samego wywołania łącza, który wygenerował plik .pgd.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie Menedżera PGO spowoduje dodanie pgcFile.pgc pgdFile.pgd sześć razy.  
  
```  
pgomgr /merge:6 pgcFile.pgc pgdFile.pgd  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie Menedżera PGO zostaną dodane do pgdFile.pgd dwa razy dla każdego pliku .pgc pgcFile1.pgc i pgcFile2.pgc.  
  
```  
pgomgr /merge:2 pgcFile1.pgc pgcFile2.pgc pgdFile.pgd  
```  
  
## <a name="example"></a>Przykład  
 Menedżer PGO jest uruchamiany bez pliku .pgc przeszuka katalog lokalny dla wszystkich plików .pgc, które mają taką samą nazwę jak plik .pgd dołączony znakiem wykrzyknika (!), następuje dowolnych znaków. Jeśli katalog lokalny ma test.pgd pliki, test!1.pgc test2.pgc i test!hello.pgc i następujące polecenie jest uruchamiane z katalogu lokalnego, następnie test!1.pgc i test!hello.pgc zostaną scalone test.pgd.  
  
```  
pgomgr /merge test.pgd  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Optymalizacje sterowane profilem](../../build/reference/profile-guided-optimizations.md)