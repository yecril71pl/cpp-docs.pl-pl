---
title: Strategie internacjonalizacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
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
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 20e4d7b067daedcbc5ce065c096e561dbf932ac1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33856599"
---
# <a name="internationalization-strategies"></a>Strategie internacjonalizacji
W zależności od systemów operacyjnych i rynkach masz kilka strategie internacjonalizacji:  
  
-   Aplikacja używa Unicode.  
  
     Korzystać z funkcji specyficznych dla Unicode i wszystkie znaki są 16 bitów dwubajtowe (mimo że można użyć znaków ANSI w niektórych części programu do celów specjalnych). Biblioteki wykonawcze języka C udostępnia funkcje, makra i typy danych dla programowania tylko Unicode. MFC jest całkowicie włączone Unicode.  
  
-   Aplikacja używa MBCS i można je uruchomić na dowolnej platformie Win32.  
  
     Możesz użyć funkcji MBCS. Ciągi mogą zawierać znaki jednobajtowe i znaki dwubajtowe. Biblioteki wykonawcze języka C udostępnia funkcje, makra i typy danych dla programowania MBCS — tylko do. MFC jest całkowicie włączone MBCS.  
  
-   Kod źródłowy aplikacji jest zapisywany przenośności pełną — kompilując symbolem **_unicode —** lub symbol **_MBCS** zdefiniowane, można utworzyć wersji, które należy użyć jednego. Aby uzyskać więcej informacji, zobacz [mapowania zwykłego tekstu w pliku Tchar.h](../text/generic-text-mappings-in-tchar-h.md).  
  
     Można użyć pełni dostosowane C czasu wykonywania funkcji, makra i danych typów. Elastyczność MFC obsługuje jedną z następujących strategii.  
  
 W pozostałej części w tych tematach skupić się na pisanie kodu całkowicie przenośny, który może stworzyć jako Unicode lub MBCS.  
  
## <a name="see-also"></a>Zobacz też  
 [Unicode i MBCS](../text/unicode-and-mbcs.md)   
 [Ustawienia regionalne i strony kodowe](../text/locales-and-code-pages.md)