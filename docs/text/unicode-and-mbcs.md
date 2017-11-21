---
title: Unicode i MBCS | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: _mbcs
dev_langs: C++
helpviewer_keywords:
- MBCS [C++], Unicode
- MFC [C++], character sets
- character sets [C++], multibyte
- run-time libraries [C++], language portability
- character sets [C++], Unicode
- Unicode [C++], MFC and C run-time functions
- multibyte characters [C++]
- runtime [C++], language portability
ms.assetid: 677baec6-71b4-4579-94df-64f18bc117c4
caps.latest.revision: "9"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: b46158795c91c0c1982e50f56d8961106b952076
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="unicode-and-mbcs"></a>Unicode i MBCS
Biblioteka Microsoft Foundation Classes (MFC), biblioteki wykonawczej języka C w języku Visual C++ i środowisko projektowe Visual C++ są włączone do pomocy programu programowanie międzynarodowe. Udostępniają one:  
  
-   Obsługa standardu Unicode w systemie Windows 2000 (dawniej systemu Windows NT). Unicode jest obecnie standardowym i powinna być używana, jeśli to możliwe.  
  
     Unicode jest znakiem 16-bitowego kodowania, zapewniając za mało kodowania dla wszystkich języków. Wszystkie znaki ASCII są uwzględniane w Unicode jako poszerzył znaków.  
  
    > [!NOTE]
    >  Standardu Unicode nie jest obsługiwana w systemie Windows 95, Windows 98 lub Windows Millennium Edition.  
  
-   Obsługa formularza zestawu znaków wielobajtowych (MBCS) o nazwie zestaw znaków dwubajtowych (DBCS) na wszystkich platformach.  
  
     Dwubajtowe składają się z 1 lub 2 bajty. Niektóre zakresów bajtów są zarezerwowane do użytku w realizacji bajtów. Bajtu Określa, czy go i następny bajt dziennik obejmują pojedynczy znak 2 bajtów na poziomie. Użytkownik musi zachować informacje o bajtów, które są realizacji bajtów. W określonym zestawie znaków wielobajtowych bajtów realizacji mieścić się w pewnym, jak bajtów dziennik. Gdy nakładają się tych zakresów, może być konieczne do oceny kontekst do określenia, czy danego typu byte działa jako bajtu lub bajt.  
  
-   Obsługa narzędzia, które upraszczają programowanie MBCS aplikacje napisane dla międzynarodową.  
  
     Uruchomienia włączone MBCS wersji systemu operacyjnego Windows, programistycznej Visual C++ — w tym Edytor kodu źródłowego zintegrowanego, debugera i narzędzia wiersza polecenia — jest całkowicie włączone MBCS. Aby uzyskać więcej informacji, zobacz [Obsługa MBCS w języku Visual C++](../text/mbcs-support-in-visual-cpp.md).  
  
> [!NOTE]
>  W tej dokumentacji MBCS jest używany do opisania wszystkich Obsługa standardu Unicode znaki wielobajtowe. W programie Visual C++ MBCS zawsze oznacza zestawów znaków Dwubajtowych. Zestawy znaków większa niż 2 bajty nie są obsługiwane.  
  
 Zgodnie z definicją zestawu znaków ASCII jest podzbiorem wszystkich zestawów znaków wielobajtowych. W wielu zestawów znaków wielobajtowych każdego znaku w zakresie 0x00 - 0x7F jest taki sam jak znak, który ma taką samą wartość zestawu znaków ASCII. Na przykład w ciągach znaków ASCII i MBCS, 1-bajtowy **NULL** znaków ('\0') ma wartość 0x00 i wskazuje znak końcowy null.  
  
## <a name="see-also"></a>Zobacz też  
 [Tekst i ciągi](../text/text-and-strings-in-visual-cpp.md)   
 [Włączanie internacjonalizacji](../text/international-enabling.md)