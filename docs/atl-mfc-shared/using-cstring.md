---
title: Przy użyciu obiektu CString | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CString objects, C++ string manipulation
- CString objects, reference counting
- CString class (Visual C++)
ms.assetid: ed018aaf-8b10-46f9-828c-f9c092dc7609
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 591a319671ea42236af5ae7e80ea1cb94c3c446c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="using-cstring"></a>Przy użyciu obiektu CString
Tematy w tej sekcji opisano sposób programu z `CString`. Dokumentacja odwołanie `CString` , zobacz dokumentację [CStringT](../atl-mfc-shared/reference/cstringt-class.md).  
  
 Aby użyć `CString`, obejmują `atlstr.h` nagłówka.  
  
 `CString`, `CStringA`, I `CStringW` klasy są specjalizacji szablonu klasy o nazwie [CStringT](../atl-mfc-shared/reference/cstringt-class.md) na podstawie typu danych znakowych ich obsługi.  
  
 A `CStringW` zawiera obiekt `wchar_t` wpisz i obsługuje ciągów Unicode. A `CStringA` zawiera obiekt `char` typu i obsługuje jednobajtowe i wielobajtowe ciągów (MBCS). A `CString` obiekt obsługuje albo `char` typu lub `wchar_t` typu, w zależności od tego, czy `MBCS` symbolu lub `UNICODE` symbol jest zdefiniowany w czasie kompilacji.  
  
 A `CString` obiekt przechowuje dane znakowe w `CStringData` obiektu. `CString` akceptuje `null`-zakończone stylu języka C ciągów, ale nie zachowuje `null` znak w znaku przechowywanych danych. Zamiast tego `CString` długość ciągu ścieżki. `CString` Podaj terminatorem null, gdy jej eksportuje ciąg stylu języka C. Możesz wstawić `null` w `CString`, ale może dać nieoczekiwane wyniki.  
  
 Następujący zestaw klas ciąg może być używany bez konsolidacji biblioteki MFC z lub bez obsługi CRT: `CAtlString`, `CAtlStringA`, i `CAtlStringW`.  
  
 `CString` jest używany w projektów natywnych. Dla kodu zarządzanego (C + +/ CLI) projektów, użyj `System::String`.  
  
 Aby dodać więcej możliwości niż `CString`, `CStringA`, lub `CStringW` aktualnie oferować, należy utworzyć podklasy `CStringT` zawierający dodatkowe funkcje.  
  
 Poniższy kod przedstawia sposób tworzenia `CString` i wydrukuj go do wyjścia standardowego:  
  
```cpp  
#include <atlstr.h>  
  
int main() {  
    CString aCString = CString(_T("A string"));  
    _tprintf(_T("%s"), (LPCTSTR) aCString);  
}  
```  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Podstawowe operacje na obiekcie CString](../atl-mfc-shared/basic-cstring-operations.md)  
 Opisuje podstawowe `CString` operacje, w tym tworzenie obiektów z C ciągi literału, uzyskiwanie dostępu do poszczególnych znaków `CString`dwa obiekty łączenie i porównywanie `CString` obiektów.  
  
 [Zarządzanie danymi ciągów](../atl-mfc-shared/string-data-management.md)  
 Omówienie korzystania z Unicode i MBCS z `CString`.  
  
 [CString — semantyka](../atl-mfc-shared/cstring-semantics.md)  
 Wyjaśniono, jak `CString` obiekty są używane.  
  
 [CString — operacje odnoszące się do ciągów stylu C](../atl-mfc-shared/cstring-operations-relating-to-c-style-strings.md)  
 W tym artykule opisano, manipulowanie zawartość `CString` obiektów, takich jak ciąg zerem w stylu języka C.  
  
 [Alokowanie i zwalnianie pamięci dla BSTR](../atl-mfc-shared/allocating-and-releasing-memory-for-a-bstr.md)  
 Omówienie korzystania z pamięci dla `BSTR` i obiektów COM.  
  
 [CString — oczyszczanie wyjątku](../atl-mfc-shared/cstring-exception-cleanup.md)  
 Wyjaśniono, który jawne Oczyszczanie 3.0 MFC i później nie jest już konieczne.  
  
 [CString — przekazywanie argumentów](../atl-mfc-shared/cstring-argument-passing.md)  
 Wyjaśniono, jak przekazać do funkcji cstring — obiekty i sposób zwracania `CString` obiektów z funkcji.  
  
 [Obsługa Unicode i Multibyte Character Set (MBCS)](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)  
 W tym artykule omówiono, jak MFC jest włączona dla Unicode i MBCS obsługuje.  
  
## <a name="reference"></a>Tematy pomocy  
 [CStringT](../atl-mfc-shared/reference/cstringt-class.md)  
 Zawiera informacje na temat `CStringT` klasy.  
  
 [CSimpleStringT, klasa](../atl-mfc-shared/reference/csimplestringt-class.md)  
 Zawiera informacje na temat `CSimpleStringT` klasy.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Ciągi (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)  
 Zawiera linki do tematów opisujących kilka sposobów zarządzania danych ciągu.  
  
 [Ciągi (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)

