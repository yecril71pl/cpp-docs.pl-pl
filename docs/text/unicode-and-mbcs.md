---
title: Unicode i MBCS | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- _mbcs
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: af5f782a337c7dc4b85c25006d7a1470034b92b4
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42584274"
---
# <a name="unicode-and-mbcs"></a>Unicode i MBCS
Biblioteki Microsoft Foundation Classes (MFC), biblioteki wykonawczej języka C dla języka Visual C++ i Środowisko deweloperskie Visual C++ są włączone do pomocy usługi programowanie międzynarodowe. Zapewniają one:  
  
-   Obsługa standardu Unicode na Windows. Unicode jest bieżące normy i powinny być używane, jeśli to możliwe.  
  
     Unicode jest znak 16-bitowych, kodowania, zapewniając wystarczającą ilość kodowania dla wszystkich języków. Wszystkie znaki ASCII znajdują się w formacie Unicode w postaci poszerzył znaków.  
  
-   Pomoc techniczna dla formularza zestaw znaków wielobajtowych (MBCS) o nazwie zestawu znaków dwubajtowych (DBCS) na wszystkich platformach.  
  
     Dwubajtowe składają się z 1 lub 2 bajtów. Niektóre zakresów bajtów są ustawiane przeznaczone do użytku jako wiodące bajty. Bajt wiodący Określa, że jej i następujących bajt obejmują pojedynczy znak 2 bajtów na poziomie. Użytkownik musi zachować informacje o bajtów, które są wiodące bajty. W określonym zestawie znaków wielobajtowych wiodące bajty mieszczą się w pewnym zakresie, tak jak bajtów dziennika. Podczas tych zakresów zachodziły na siebie, może być konieczne do oceny kontekstu, aby określić, czy dany bajtów działa jako bajt wiodący lub bajt.  
  
-   Obsługa narzędzia, które upraszczają programowanie MBCS aplikacji napisanych na rynki międzynarodowe.  
  
     Podczas uruchamiania na włączone MBCS wersji systemu operacyjnego Windows, system programowania języka Visual C++ — m.in. Edytor kodu źródłowego zintegrowany debuger i narzędzia wiersza polecenia — jest całkowicie włączone MBCS. Aby uzyskać więcej informacji, zobacz [Obsługa MBCS w programie Visual C++](../text/mbcs-support-in-visual-cpp.md).  
  
> [!NOTE]
>  W tej dokumentacji MBCS jest używany do opisania innego niż Unicode Obsługa wszystkich znaków wielobajtowych. MBCS w programie Visual C++ zawsze jest to znaków Dwubajtowych. Większa niż 2 bajty nie są obsługiwane zestawy znaków.  
  
 Zgodnie z definicją zestaw znaków ASCII jest podzestawem wszystkich zestawów znaków wielobajtowych. W wielu zestawów znaków wielobajtowych każdy znak w zakresie 0x00 - 0x7F jest taka sama jak znak, który ma taką samą wartość w zestawie znaków ASCII. Na przykład w ciągach znaków ASCII i znaków MBCS, 1-bajtowe znakiem NULL (\0) ma wartość 0x00 i wskazuje kończącego znaku null.  
  
## <a name="see-also"></a>Zobacz też  
 [Tekst i ciągi](../text/text-and-strings-in-visual-cpp.md)   
 [Włączanie internacjonalizacji](../text/international-enabling.md)