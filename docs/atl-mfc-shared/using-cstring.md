---
title: Użycie CString
ms.date: 06/18/2018
helpviewer_keywords:
- CString objects, C++ string manipulation
- CString objects, reference counting
- CString class (Visual C++)
ms.assetid: ed018aaf-8b10-46f9-828c-f9c092dc7609
ms.openlocfilehash: 8ebf3441c7d8856fe412e2efed4c717b01ced362
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219017"
---
# <a name="using-cstring"></a>Użycie CString

W tematach w tej sekcji opisano, jak programować za pomocą programu `CString` . Aby uzyskać dokumentację referencyjną dotyczącą `CString` klasy, zobacz dokumentację dotyczącą [CStringT](../atl-mfc-shared/reference/cstringt-class.md).

Aby użyć `CString` , Dołącz `atlstr.h` nagłówek.

`CString`Klasy, `CStringA` i `CStringW` są specjalizacjami szablonu klasy o nazwie [CStringT](../atl-mfc-shared/reference/cstringt-class.md) w oparciu o typ obsługiwanych przez nich danych znakowych.

`CStringW`Obiekt zawiera **`wchar_t`** Typ i obsługuje ciągi Unicode. `CStringA`Obiekt zawiera **`char`** Typ i obsługuje ciągi jednobajtowe i wielobajtowe (MBCS). `CString`Obiekt obsługuje **`char`** Typ lub **`wchar_t`** Typ, w zależności od tego, czy symbol MBCS lub symbol Unicode jest zdefiniowany w czasie kompilacji.

`CString`Obiekt zachowuje dane znakowe w `CStringData` obiekcie. `CString`akceptuje ciągi w stylu C o wartości NULL. `CString`śledzi długość ciągu w celu zwiększenia wydajności, ale zachowuje także znak NULL w danych przechowywanych znaków do obsługi konwersji do LPCWSTR. `CString`uwzględnia terminator wartości null podczas eksportowania ciągu w stylu C. Można wstawić wartość NULL w innych lokalizacjach w `CString` , ale może to spowodować nieoczekiwane wyniki.

Następujący zestaw klas ciągów może być używany bez konsolidacji biblioteki MFC z obsługą CRT lub bez niej: `CAtlString` , `CAtlStringA` , i `CAtlStringW` .

`CString`jest używany w projektach natywnych. W przypadku projektów kodu zarządzanego (C++/CLI) Użyj `System::String` .

Aby dodać więcej możliwości niż `CString` , `CStringA` lub `CStringW` obecnie oferta, należy utworzyć podklasę zawierającą `CStringT` dodatkowe funkcje.

Poniższy kod pokazuje, jak utworzyć `CString` a i wydrukować go do wyjścia standardowego:

```cpp
#include <atlstr.h>

int main() {
    CString aCString = CString(_T("A string"));
    _tprintf(_T("%s"), (LPCTSTR) aCString);
}
```

## <a name="in-this-section"></a>W tej sekcji

[Podstawowe operacje CString](../atl-mfc-shared/basic-cstring-operations.md)<br/>
Opisuje `CString` operacje podstawowe, w tym tworzenie obiektów z ciągów literałów języka C, uzyskiwanie dostępu do pojedynczych znaków w `CString` , łączenie dwóch obiektów i porównywanie `CString` obiektów.

[Ciąg Zarządzanie danymi](../atl-mfc-shared/string-data-management.md)<br/>
Omawia użycie standardu Unicode i MBCS z `CString` .

[Semantyka CString](../atl-mfc-shared/cstring-semantics.md)<br/>
Wyjaśnia, jak `CString` obiekty są używane.

[Operacje CString odnoszące się do ciągów w stylu C](../atl-mfc-shared/cstring-operations-relating-to-c-style-strings.md)<br/>
Opisuje manipulowanie zawartością `CString` obiektu, taki jak ciąg w stylu C zakończony znakiem null.

[Przydzielanie i zwalnianie pamięci dla typu BSTR](../atl-mfc-shared/allocating-and-releasing-memory-for-a-bstr.md)<br/>
W tym artykule omówiono użycie pamięci dla obiektów BSTR i COM.

[CString — oczyszczanie wyjątków](../atl-mfc-shared/cstring-exception-cleanup.md)<br/>
Wyjaśnia, że jawne czyszczenie w MFC 3,0 i nowszych nie jest już konieczne.

[Przekazywanie argumentu CString](../atl-mfc-shared/cstring-argument-passing.md)<br/>
Wyjaśnia, jak przekazać obiekty CString do funkcji i jak zwracać `CString` obiekty z funkcji.

[Obsługa zestawu znaków Unicode i wielobajtowego (MBCS)](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)<br/>
W tym artykule omówiono, w jaki sposób MFC jest włączone dla obsługi standardu Unicode i MBCS.

## <a name="reference"></a>Dokumentacja

[CStringT](../atl-mfc-shared/reference/cstringt-class.md)<br/>
Zawiera informacje referencyjne dotyczące `CStringT` klasy.

[Klasa CSimpleStringT](../atl-mfc-shared/reference/csimplestringt-class.md)<br/>
Zawiera informacje referencyjne dotyczące `CSimpleStringT` klasy.

## <a name="related-sections"></a>Sekcje pokrewne

[Ciągi (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
Zawiera łącza do tematów, które opisują kilka sposobów zarządzania danymi ciągu.

[Ciągi (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)
