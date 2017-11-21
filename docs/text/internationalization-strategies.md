---
title: Strategie internacjonalizacji | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- globalization [C++], character sets
- language-portable code [C++]
- MBCS [C++], internationalization strategies
- Windows API [C++], international programming strategies
- Win32 [C++], international programming strategies
- Unicode [C++], globalizing applications
- character sets [C++], international programming strategies
- localization [C++], character sets
ms.assetid: b09d9854-0709-4b9a-a00c-b0b8bc4199b1
caps.latest.revision: "8"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 944ba06bd7b3d81abb2ab431494096f9ade77574
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="internationalization-strategies"></a>Strategie internacjonalizacji
W zależności od systemów operacyjnych i rynkach masz kilka strategie internacjonalizacji:  
  
-   Aplikacja używa standardu Unicode i dlatego jest uruchamiana w systemie Windows 2000 i Windows NT, ale nie w systemie Windows 95 lub Windows 98.  
  
     Korzystać z funkcji specyficznych dla Unicode i wszystkie znaki są 16 bitów dwubajtowe (mimo że można użyć znaków ANSI w niektórych części programu do celów specjalnych). Biblioteki wykonawcze języka C udostępnia funkcje, makra i typy danych dla programowania tylko Unicode. MFC jest całkowicie włączone Unicode.  
  
-   Aplikacja używa MBCS i można je uruchomić na dowolnej platformie Win32.  
  
     Możesz użyć funkcji MBCS. Ciągi mogą zawierać znaki jednobajtowe i znaki dwubajtowe. Biblioteki wykonawcze języka C udostępnia funkcje, makra i typy danych dla programowania MBCS — tylko do. MFC jest całkowicie włączone MBCS.  
  
-   Kod źródłowy aplikacji jest zapisywany przenośności pełną — kompilując symbolem **_unicode —** lub symbol **_MBCS** zdefiniowane, można utworzyć wersji, które należy użyć jednego. Aby uzyskać więcej informacji, zobacz [mapowania zwykłego tekstu w pliku Tchar.h](../text/generic-text-mappings-in-tchar-h.md).  
  
-   Aplikacja używa biblioteki otoki dla brakujących funkcje Unicode w systemie Windows 95, Windows 98 i Windows ME, tak jak to opisano w [projektowania tylko jednej aplikacji Unicode działa zarówno Windows 98 i Windows 2000](http://go.microsoft.com/fwlink/p/?LinkId=250770). Otoki biblioteki są również dostępne w rynku.  
  
     Można użyć pełni dostosowane C czasu wykonywania funkcji, makra i danych typów. Elastyczność MFC obsługuje jedną z następujących strategii.  
  
 W pozostałej części w tych tematach skupić się na pisanie kodu całkowicie przenośny, który może stworzyć jako Unicode lub MBCS.  
  
## <a name="see-also"></a>Zobacz też  
 [Unicode i MBCS](../text/unicode-and-mbcs.md)   
 [Ustawienia regionalne i strony kodowe](../text/locales-and-code-pages.md)