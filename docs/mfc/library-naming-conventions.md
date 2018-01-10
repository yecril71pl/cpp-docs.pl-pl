---
title: Konwencje nazewnictwa biblioteki | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- NAFXCW.LIB [MFC]
- libraries [MFC], static
- coding conventions [MFC], MFC library names
- NAFXCWD.LIB [MFC]
- console applications [MFC], MFC library versions
- naming conventions [MFC], MFC object code libraries
- object code libraries, MFC naming conventions
- object code libraries
- conventions [MFC], MFC library names
- MFC libraries, naming conventions
ms.assetid: 39fe7d93-5a14-4c6a-b16c-bf318fa01278
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 14e217b3cfd9f3618046cf1a0ca825eb2e6492f2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="library-naming-conventions"></a>Konwencje nazewnictwa bibliotek
Kod obiektu biblioteki MFC, użyj następujących konwencji nazewnictwa. Nazwy bibliotek mają następującą postać  
  
 *u*AFX*c*W*d*. LIB  
  
 gdzie kursywą małe litery są symbole zastępcze Specyfikatory, których znaczenie przedstawiono w poniższej tabeli:  
  
### <a name="library-naming-conventions"></a>Konwencje nazewnictwa bibliotek  
  
|Specyfikator|Wartości i znaczenia|  
|---------------|-------------------------|  
|*u*|ANSI (N) lub Unicode (U)|  
|*c*|Typ programu do utworzenia: C = all|  
|*d*|Debugowania i wydania: D = Debug; Pomiń specyfikator wersji|  
  
 Wartość domyślna to do kompilacji debugowania aplikacji Windows ANSI na platformie Intel: NAFXCWD.Lib. Wszystkie biblioteki wymienione w poniższej tabeli znajdują się w katalogu \atlmfc\lib wbudowane.  
  
### <a name="static-link-library-naming-conventions"></a>Biblioteki statyczne konwencje nazewnictwa  
  
|Biblioteka|Opis|  
|-------------|-----------------|  
|NAFXCW.LIB|Biblioteka dołączana statycznie MFC, wersja|  
|NAFXCWD.LIB|Biblioteka dołączana statycznie MFC, wersja do debugowania|  
|UAFXCW. LIB|Biblioteka dołączana statycznie MFC z obsługą Unicode, wersja|  
|UAFXCWD. LIB|Biblioteka dołączana statycznie MFC z obsługą Unicode, wersja do debugowania|  
  
> [!NOTE]
>  Jeśli musisz utworzyć wersję biblioteki, zobacz plik Readme.Txt w katalogu \atlmfc\src\mfc. Ten plik zawiera opis przy użyciu dostarczonego pliku reguł programu make z NMAKE.  
  
 Aby uzyskać więcej informacji, zobacz [konwencje nazewnictwa bibliotek MFC dll](../build/naming-conventions-for-mfc-dlls.md) i [Unicode wersje biblioteki MFC](../mfc/unicode-in-mfc.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wersje biblioteki MFC](../mfc/mfc-library-versions.md)

