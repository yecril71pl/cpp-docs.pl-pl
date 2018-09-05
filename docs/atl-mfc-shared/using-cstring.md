---
title: Użycie CString | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 06/18/2018
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
ms.openlocfilehash: c97ca07e06da3663dfd0a06a125f361b4e4dc591
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43758033"
---
# <a name="using-cstring"></a>Użycie CString

Tematy w tej sekcji opisano, jak programowanie z `CString`. Dla dokumentacji o `CString` klasy, zobacz dokumentację [CStringT](../atl-mfc-shared/reference/cstringt-class.md).

Aby użyć `CString`, obejmują `atlstr.h` nagłówka.

`CString`, `CStringA`, I `CStringW` klasy są specjalizacje szablonu klasy o nazwie [CStringT](../atl-mfc-shared/reference/cstringt-class.md) na podstawie typu danych znakowych obsługują.

A `CStringW` obiekt zawiera **wchar_t** wpisz i obsługuje ciągów Unicode. A `CStringA` obiekt zawiera **char** typu i obsługuje wielobajtowych i jednobajtowych ciągów (znaków MBCS). A `CString` obiekt obsługuje **char** typu lub `wchar_t` typu, w zależności od tego, czy MBCS symbol lub symboli UNICODE jest zdefiniowana w czasie kompilacji.

A `CString` obiekt przechowuje dane znakowe w `CStringData` obiektu. `CString` akceptuje ciągi stylu C zakończony znakiem NULL. `CString` śledzi ciąg długość zwiększyć wydajność, ale także zachowuje znak NULL w danych znakowych przechowywanych do obsługi konwersji do LPCWSTR. `CString` dołącza terminatora null, podczas eksportuje ona ciąg stylu C. Możesz wstawić wartość NULL w innych miejscach w `CString`, ale może on powodować nieoczekiwane rezultaty.

Następujący zestaw klas ciągów może być używana bez konsolidacji biblioteki MFC, z lub bez obsługi CRT: `CAtlString`, `CAtlStringA`, i `CAtlStringW`.

`CString` jest używana w natywnych projektów. Dla kodu zarządzanego (C + +/ CLI) projektów, użyj `System::String`.

Aby dodać więcej funkcji niż `CString`, `CStringA`, lub `CStringW` aktualnie oferować, należy utworzyć podklasę klasy `CStringT` zawierający dodatkowe funkcje.

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
W tym artykule opisano podstawowe `CString` operacji, takich jak tworzenie obiektów z ciągami tekstowymi C, uzyskiwanie dostępu do poszczególnych znaków `CString`, złączenie dwa obiekty i porównywanie `CString` obiektów.

[Zarządzanie danymi ciągów](../atl-mfc-shared/string-data-management.md)  
Omawia przy użyciu standardów Unicode i MBCS — za pomocą `CString`.

[CString — semantyka](../atl-mfc-shared/cstring-semantics.md)  
Wyjaśnia, jak `CString` obiekty są używane.

[CString — operacje odnoszące się do ciągów stylu C](../atl-mfc-shared/cstring-operations-relating-to-c-style-strings.md)  
W tym artykule opisano, manipulowanie zawartością `CString` obiektów, takich jak ciąg stylu C zakończony znakiem null.

[Alokowanie i zwalnianie pamięci dla BSTR](../atl-mfc-shared/allocating-and-releasing-memory-for-a-bstr.md)  
W tym artykule omówiono, użycie pamięci dla BSTR i COM obiektów.

[CString — oczyszczanie wyjątku](../atl-mfc-shared/cstring-exception-cleanup.md)  
Wyjaśniono, że jawnego usuwania z pamięci w MFC 3.0 i nowszej jest już konieczne.

[CString — przekazywanie argumentów](../atl-mfc-shared/cstring-argument-passing.md)  
Wyjaśnia, jak przekazać cstring — obiekty do funkcji oraz sposób zwracania `CString` obiektów z usługi functions.

[Obsługa Unicode i Multibyte Character Set (MBCS)](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)  
W tym artykule omówiono, jak MFC jest włączona dla standardu Unicode i MBCS pomocy technicznej.

## <a name="reference"></a>Tematy pomocy

[CStringT](../atl-mfc-shared/reference/cstringt-class.md)  
Zawiera informacje na temat `CStringT` klasy.

[CSimpleStringT, klasa](../atl-mfc-shared/reference/csimplestringt-class.md)  
Zawiera informacje na temat `CSimpleStringT` klasy.

## <a name="related-sections"></a>Sekcje pokrewne

[Ciągi (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)  
Zawiera łącza do tematów opisujących kilka sposobów zarządzania danych ciągu.

[Ciągi (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)

