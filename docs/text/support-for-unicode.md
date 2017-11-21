---
title: "Obsługa formatu Unicode | Dokumentacja firmy Microsoft"
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
- portable data types [MFC]
- Unicode [C++]
- wide characters [C++], about wide characters
- character sets [C++], Unicode
- localization [C++], character sets
- Unicode [C++], installing support
ms.assetid: 180f1d10-8543-4f79-85ce-293d3cb443bb
caps.latest.revision: "10"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: b58901f213d5e69eb50ad449a87266736fba0af7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="support-for-unicode"></a>Obsługa formatu Unicode
Unicode jest specyfikacją do obsługi wszystkich zestawów znaków, łącznie z tymi, które nie mogą być reprezentowane w tylko jednego bajtu. Jeśli programowanie międzynarodowe rynku zalecane jest użycie obu Unicode lub [zestawów znaków wielobajtowych](../text/support-for-multibyte-character-sets-mbcss.md) (zestawy MBCS) lub Włącz program, można je tworzyć bądź zmiana przełącznika.  
  
 Znaków dwubajtowych jest kodem 2-bajtowych wartości znakowych wielu języków. Większość znaków użytych w nowoczesnych przetwarzania danych na całym świecie, tym techniczne symboli i znaków specjalnych publikowania, może być reprezentowany według specyfikacji Unicode jako znaków dwubajtowych. Znaki, których nie można przedstawić w jednego znaku dwubajtowe ma być reprezentowane w parę Unicode za pomocą funkcji zastępcza Unicode. Ponieważ każdy znaków typu wide jest reprezentowana w o stałym rozmiarze 16 bitów, przy użyciu znaki dwubajtowe upraszcza programowanie z użyciem zestawu znaków międzynarodowych.  
  
 Ciąg znaków dwubajtowych jest reprezentowany jako **[wchar_t]** tablicy i jest wskazywana przez `wchar_t*` wskaźnika. Dowolny znak ASCII może być reprezentowana jako znaków dwubajtowych, prefiksu litera na znak. Na przykład L '\0' to przerywanie dwubajtowe (16-bitowy) **NULL** znaków. Podobnie dowolny ciąg ASCII literał może być reprezentowana jako literału ciągu znaków dwubajtowych, dodając litera na literał ASCII (L "Hello").  
  
 Ogólnie rzecz biorąc znaki dwubajtowe zająć więcej miejsca w pamięci, niż znaków wielobajtowych, ale są szybsze do procesu. Ponadto tylko jeden ustawień regionalnych może być reprezentowany w czasie w kodowaniu wielobajtowe, natomiast zestawy wszystkich znaków w świecie są jednocześnie reprezentowane przez reprezentacja Unicode.  
  
 Struktura MFC jest obsługą Unicode w całym i wykonuje MFC Unicode włączenie przy użyciu makra przenośne, jak pokazano w poniższej tabeli.  
  
### <a name="portable-data-types-in-mfc"></a>Przenośne typy danych w MFC  
  
|Typ danych inne niż przenośna|Zastępuje to makro|  
|-----------------------------|----------------------------|  
|`char`|_**TCHAR —**|  
|**CHAR\***, **LPSTR (Win32 typu danych)**|`LPTSTR`|  
|**Const char\*, LPCSTR (Win32 typu danych)**|`LPCTSTR`|  
  
 Klasa `CString` używa **_tchar —** podstawowym i zapewnia łatwe konwersje konstruktory i operatory. Większość operacje na ciągach standardu Unicode można pisać przy użyciu tej samej logiki, używany do obsługi zestawu znaków ANSI systemu Windows z wyjątkiem tego, że podstawowa jednostka operacji jest znakiem 16-bitową zamiast bajtów 8-bitową. W przeciwieństwie do pracy z zestawów znaków wielobajtowych, nie trzeba (i nie powinien) Traktuj znaków Unicode, tak jakby był on dwa różne bajty.  
  
## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?  
  
-   [Zainstaluj obsługę standardu Unicode za pomocą MFC](../mfc/unicode-in-mfc.md)  
  
-   [Włącz Unicode w programach](../text/international-enabling.md)  
  
-   [Włącz zarówno Unicode i MBCS w programach](../text/internationalization-strategies.md)  
  
-   [Używaj Unicode do utworzenia programu międzynarodowych](../text/unicode-programming-summary.md)  
  
-   [Poznaj korzyści ze znaków Unicode, w tym, jak przy użyciu Unicode sprawia, że program większą wydajność w systemie Windows 2000](../text/benefits-of-character-set-portability.md)  
  
-   [Użyj wmain, do programu można przekazać argumenty znaków dwubajtowych](../text/support-for-using-wmain.md)  
  
-   [Widoczne jest podsumowanie programowania Unicode](../text/unicode-programming-summary.md)  
  
-   [Więcej informacji na temat mapowania zwykłego tekstu przenośności szerokość bajtów](../text/generic-text-mappings-in-tchar-h.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Tekst i ciągi](../text/text-and-strings-in-visual-cpp.md)   
 [Obsługa używania funkcji wmain](../text/support-for-using-wmain.md)