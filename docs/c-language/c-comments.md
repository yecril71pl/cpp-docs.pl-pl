---
title: Komentarze języka C | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 06/25/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- code comments, C code
- comments, documenting code
- comments, C code
- /* */ comment delimiters
- comments
ms.assetid: 0f5f2825-e673-49e7-8669-94e2f5294989
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c2eccff8ab582270f766fdbcb448fdb91145e348
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37121747"
---
# <a name="c-comments"></a>Komentarze języka C
"comment" jest sekwencji znaków, zaczynając od kombinacji kreską ułamkową/gwiazdki (<b>/\*</b>) który jest traktowany jako pojedynczy znak odstępu przez kompilator, a w przeciwnym razie jest ignorowana. Komentarz może zawierać dowolną kombinację znaków z zestawu można przedstawić znaku, łącznie ze znakami nowego wiersza, z wyłączeniem ogranicznika "końca komentarza" (<b>\*/</b>). Komentarze mogą zajmować więcej niż jeden wiersz, ale nie mogą być zagnieżdżone.  
  
 Komentarze mogą pojawić się wszędzie tam, gdzie dozwolone są odstępy. Ponieważ kompilator traktuje komentarz jako pojedynczy odstęp, nie można dołączać komentarzy w obrębie tokenów. Kompilator ignoruje znaki w komentarzu.  
  
 Komentarze służą do dokumentowania kodu. W tym przykładzie występuje komentarz akceptowany przez kompilator:  
  
```  
/* Comments can contain keywords such as  
   for and while without generating errors. */  
```  
  
 Komentarze mogą pojawić się w tym samym wierszu, co instrukcja kodu:  
  
```  
printf( "Hello\n" );  /* Comments can go here */  
```  
  
 Można poprzedzać funkcje lub moduły programu opisowym blokiem komentarza:  
  
```  
/* MATHERR.C illustrates writing an error routine   
 * for math functions.   
 */   
```  
  
 Ponieważ komentarze nie mogą zawierać zagnieżdżonych komentarzy, ten przykład wygeneruje błąd:  
  
```  
/* Comment out this routine for testing   
  
   /* Open file */  
    fh = _open( "myfile.c", _O_RDONLY );  
    .  
    .  
    .  
 */  
```  
  
 Ten błąd występuje, ponieważ kompilator rozpoznaje pierwsze `*/`, po wyrazach `Open file`, jako koniec komentarza. Próbuje on przetworzyć pozostały tekst i generuje błąd, gdy napotka `*/` poza komentarzem.  
  
 Podczas gdy można używać komentarzy do oznaczenia pewnych linii kodu jako nieaktywnych dla celów testowych, dyrektywy preprocesora `#if`, `#endif` i kompilacja warunkowa są przydatną alternatywą dla wykonania tego zadania. Aby uzyskać więcej informacji, zobacz [dyrektywy preprocesora](../preprocessor/preprocessor-directives.md) w *odwołania preprocesora*.  
  
 **Microsoft Specific**  
  
 Kompilator Microsoft obsługuje również Komentarze jednowierszowe poprzedzony przez dwa ukośniki (__//__). W przypadku kompilacji z użyciem /Za (standard ANSI), te komentarze spowodują wygenerowanie błędów. Nie można rozszerzać komentarzy do drugiego wiersza.  
  
```  
// This is a valid comment  
```  
  
 Komentarze, począwszy od dwa ukośniki (__//__) kończą się przez następny znak nowego wiersza, który nie jest poprzedzony znakiem ucieczki. W następnym przykładzie znaku nowego wiersza jest poprzedzony ukośnikiem (**\\**), tworzenie "sekwencji unikowej". Ta sekwencja ucieczki powoduje, że kompilator traktuje następny wiersz jako część poprzedniego wiersza. (Aby uzyskać więcej informacji, zobacz [sekwencji ucieczki](../c-language/escape-sequences.md).)  
  
```  
// my comment \  
    i++;   
```  
  
 W związku z tym instrukcja `i++;` jest opatrzona komentarzem.  
  
 Wartość domyślna Microsoft C to, czy są włączone rozszerzenia Microsoft. Aby wyłączyć te rozszerzenia, użyj /Za.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Tokeny języka C](../c-language/c-tokens.md)
