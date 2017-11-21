---
title: "Interpretacja wielobajtowych sekwencji znaków | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.character.multibyte
dev_langs: C++
helpviewer_keywords: MBCS [C++], locale code page
ms.assetid: da9150de-70ea-4d2f-90e6-ddb9202dd80b
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ca454b0087bd9cc1b8ded6f7b2d4ccb201373dc4
ms.sourcegitcommit: 2a5d0e9e6829150cbc22c6de3395ec13008e3266
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="interpretation-of-multibyte-character-sequences"></a>Interpretacja wielobajtowych sekwencji znaków
Większość procedur znaków wielobajtowych biblioteki wykonawczej Microsoft rozpoznaje wielobajtowych sekwencji znaków odnoszących się do strony kodowe wielobajtowe. Wartość wyjściowa jest zagrożony ustawienie `LC_CTYPE` ustawienie kategorii ustawień regionalnych; zobacz [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersje tych funkcji bez `_l` Użyj sufiksu bieżące ustawienia regionalne tego zachowania zależnych od ustawień regionalnych; wersje z `_l` sufiks są identyczne, z wyjątkiem tego, aby były używane zamiast przekazany parametr ustawień regionalnych.  
  
### <a name="locale-dependent-multibyte-routines"></a>Znaki wielobajtowe procedury zależne od ustawień regionalnych  
  
|Procedura|Zastosowanie|  
|-------------|---------|  
|[_mbclen —, mblen —, _mblen_l —](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)|Sprawdzanie poprawności i zwraca liczbę bajtów w znaków wielobajtowych|  
|[strlen —, wcslen —, _mbslen —, _mbslen_l — _mbstrlen —, _mbstrlen_l —](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|Ciągi znaków wielobajtowych: Sprawdzanie poprawności każdego znaku w ciągu; Zwraca długość ciągu. Ciągi znaków typu wide: zwraca długość ciągu.|  
|[mbstowcs —, _mbstowcs_l —](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md), [mbstowcs_s —, _mbstowcs_s_l —](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|Konwertuj sekwencja znaków wielobajtowych sekwencji odpowiednie znaki dwubajtowe|  
|[mbtowc —, _mbtowc_l —](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|Konwertuj znaków wielobajtowych na odpowiednich znaków dwubajtowych|  
|[wcstombs —, _wcstombs_l —](../c-runtime-library/reference/wcstombs-wcstombs-l.md), [wcstombs_s —, _wcstombs_s_l —](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|Konwertuj do odpowiedniej sekwencji znaków wielobajtowych sekwencji znaki dwubajtowe|  
|[wctomb —, _wctomb_l —](../c-runtime-library/reference/wctomb-wctomb-l.md), [wctomb_s —, _wctomb_s_l —](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|Konwertuj znaków dwubajtowych na odpowiednich znaków wielobajtowych|  
|[mbrtoc16, mbrtoc32](../c-runtime-library/reference/mbrtoc16-mbrtoc323.md)|Konwertuj odpowiednik znaku UTF-16 lub UTF-32 znaków wielobajtowych|  
|[c16rtomb, c32rtomb](../c-runtime-library/reference/c16rtomb-c32rtomb1.md)|Konwertuj UTF-16 lub UTF-32 znaków na równoważne znaków wielobajtowych|  
  
## <a name="see-also"></a>Zobacz też  
 [Przystosowywanie do warunków międzynarodowych](../c-runtime-library/internationalization.md)   
 [Procedury czasu wykonywania według kategorii](../c-runtime-library/run-time-routines-by-category.md)