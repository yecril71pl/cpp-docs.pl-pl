---
title: Ciąg Zarządzanie danymi
ms.date: 11/04/2016
helpviewer_keywords:
- Unicode, string objects
ms.assetid: 0b53a542-eeb1-4108-9ada-6700645b6f8f
ms.openlocfilehash: 2da8967effeb6ff439cf5b3cece31f63ee77a761
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219043"
---
# <a name="string-data-management"></a>Ciąg Zarządzanie danymi

Visual C++ oferuje kilka sposobów zarządzania danymi ciągu:

- [Manipulowanie ciągami](../c-runtime-library/string-manipulation-crt.md) do pracy z ciągami zakończonymi zerem o wartości null

- Funkcje Win32 API do zarządzania ciągami

- Klasa [CStringT](../atl-mfc-shared/reference/cstringt-class.md)klasy MFC, która zapewnia elastyczność obiektów ciągów o zmiennym rozmiarze

- Klasa [CStringT](../atl-mfc-shared/reference/cstringt-class.md)klasy, która udostępnia obiekt ciągu niezależny od MFC o tej samej funkcji co`CString`

Niemal wszystkie programy pracują z danymi ciągu. Klasa MFC `CString` jest często najlepszym rozwiązaniem dla elastycznej obsługi ciągów. Począwszy od wersji 7,0, `CString` mogą być używane w programach MFC lub niezależnych od MFC. Zarówno Biblioteka wykonawcza, jak i `CString` Obsługa ciągów zawierających wielobajtowe (szerokie) znaki, jak w przypadku programowania Unicode lub MBCS.

W tym artykule opisano usługi ogólnego przeznaczenia, które Biblioteka klas zawiera powiązane z manipulowaniem ciągami. Tematy omówione w tym artykule obejmują:

- [Kodowanie Unicode i MBCS zapewniają przenośność](#_core_unicode_and_mbcs_provide_portability)

- [Wskaźniki CStrings i const char](#_core_cstrings_and_const_char_pointers)

- [Zliczanie odwołań CString](#_core_cstring_reference_counting)

Klasa [klasy CStringT](../atl-mfc-shared/reference/cstringt-class.md) zapewnia obsługę manipulowania ciągami. Jest przeznaczony do zastępowania i zwiększania funkcjonalności zwykle zapewnianej przez pakiet ciągu biblioteki wykonawczej C. `CString`Klasa dostarcza funkcje składowe i operatory dla uproszczonej obsługi ciągów, podobne do tych, które znajdują się w warstwie Podstawowa. Klasa zawiera również konstruktory i operatory służące do konstruowania, przypisywania i porównywania `CString` typów danych w standardowym ciągu języka C++. Ponieważ `CString` nie pochodzi od `CObject` , można używać `CString` obiektów niezależnie od Biblioteka MFC (MFC).

`CString`obiekty podążają za "semantyką wartości". `CString`Obiekt reprezentuje unikatową wartość. `CString`Należy traktować jako rzeczywisty ciąg, nie jako wskaźnik do ciągu.

`CString`Obiekt reprezentuje sekwencję zmiennej liczby znaków. `CString`obiekty można traktować jako tablice znaków.

## <a name="unicode-and-mbcs-provide-portability"></a><a name="_core_unicode_and_mbcs_provide_portability"></a>Kodowanie Unicode i MBCS zapewniają przenośność

W przypadku biblioteki MFC w wersji 3,0 lub nowszej funkcja MFC, w tym `CString` , jest włączona dla zestawów znaków Unicode i wielobajtowych (MBCS). Ta obsługa ułatwia pisanie aplikacji przenośnych, które można kompilować dla znaków Unicode lub ANSI. Aby włączyć tę przenośność, każdy znak w `CString` obiekcie jest typu używanie TCHAR, który jest zdefiniowany jako **`wchar_t`** jeśli zdefiniujesz symbol _UNICODE podczas kompilowania aplikacji lub tak, jakby **`char`** nie. **`wchar_t`** Znak to 16 bitów w poziomie. MBCS jest włączone, Jeśli kompilujesz z symbolem zdefiniowanym _MBCS. Sama MFC jest skompilowana przy użyciu symbolu _MBCS (dla bibliotek NAFX) lub zdefiniowanego symbolu _UNICODE (dla bibliotek UAFX).

> [!NOTE]
> `CString`Przykłady w tym i towarzyszące artykuły dotyczące ciągów pokazują ciągi literałów prawidłowo sformatowane dla przenośności kodu Unicode przy użyciu makra _T, które tłumaczy ciąg literału na postać:

`L"literal string"`

> [!NOTE]
> który kompilator traktuje jako ciąg Unicode. Na przykład następujący kod:

[!code-cpp[NVC_ATLMFC_Utilities#187](../atl-mfc-shared/codesnippet/cpp/string-data-management_1.cpp)]

> [!NOTE]
> jest tłumaczony jako ciąg Unicode, Jeśli _UNICODE jest zdefiniowany lub jako ciąg ANSI. Aby uzyskać więcej informacji, zobacz [Obsługa artykułu Unicode i wielobajtowego zestawu znaków (MBCS)](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md).

`CString`Obiekt może przechowywać do INT_MAX (2 147 483 647) znaków. Typ danych używanie TCHAR służy do pobierania lub ustawiania pojedynczych znaków wewnątrz `CString` obiektu. W przeciwieństwie do tablic znaków, `CString` Klasa ma wbudowaną funkcję alokacji pamięci. Umożliwia to `CString` Automatyczne zwiększenie rozmiaru obiektów w miarę potrzeb (to oznacza, że nie trzeba martwić się o powiększanie `CString` obiektów w celu dopasowania do dłuższych ciągów).

## <a name="cstrings-and-const-char-pointers"></a><a name="_core_cstrings_and_const_char_pointers"></a>Wskaźniki CStrings i const char

`CString`Obiekt może również pełnić rolę literału ciągu w stylu C ( `PCXSTR` a, który jest taki sam jak **const char** , <strong>\*</strong> Jeśli nie jest w formacie Unicode). Operator konwersji [CSimpleStringT:: operator PCXSTR](../atl-mfc-shared/reference/csimplestringt-class.md#operator_pcxstr) umożliwia `CString` swobodne podstawianie obiektów dla wskaźników znakowych w wywołaniach funkcji. Konstruktor **CString (LPCWSTR** `pszSrc` **)** umożliwia podstawianie wskaźników znaków dla `CString` obiektów.

Nie jest podejmowana żadna próba zgięcia `CString` obiektów. W przypadku wprowadzenia dwóch `CString` obiektów zawierających `Chicago` , na przykład, znaki w `Chicago` są przechowywane w dwóch miejscach. (To może nie być prawdziwe w przyszłych wersjach MFC, dlatego nie powinna być zależą od niej).

> [!NOTE]
> Użyj funkcji Członkowskich [CSimpleStringT:: GetBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) i [CSimpleStringT:: ReleaseBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer) , jeśli chcesz bezpośrednio uzyskać dostęp do `CString` znaku jako niestałego wskaźnika.

> [!NOTE]
> Użyj funkcji składowych [CStringT:: AllocSysString](../atl-mfc-shared/reference/cstringt-class.md#allocsysstring) i [CStringT:: SetSysString](../atl-mfc-shared/reference/cstringt-class.md#setsysstring) do ALOKOWANIA i ustawiania obiektów BSTR używanych w automatyzacji (wcześniej znanych jako Automatyzacja OLE).

> [!NOTE]
> Jeśli to możliwe, Przydziel `CString` obiekty w ramce, a nie na stercie. Oszczędza to pamięć i upraszcza przekazywanie parametrów.

`CString`Klasa nie jest zaimplementowana jako Klasa kolekcji Biblioteka MFC, chociaż `CString` obiekty mogą być na pewno przechowywane jako elementy w kolekcjach.

## <a name="cstring-reference-counting"></a><a name="_core_cstring_reference_counting"></a>Zliczanie odwołań CString

Począwszy od biblioteki MFC w wersji 4,0, gdy kopiowane są obiekty [klasy CStringT](../atl-mfc-shared/reference/cstringt-class.md) , MFC zwiększa liczbę odwołań zamiast kopiowania danych. Dzięki temu przekazywanie parametrów przez wartość i zwracanie `CString` obiektów przez wartość jest bardziej wydajne. Te operacje powodują wywoływanie konstruktora kopiującego, czasami więcej niż raz. Zwiększenie liczby odwołań powoduje zmniejszenie obciążenia dla tych typowych operacji i użycie `CString` bardziej atrakcyjnej opcji.

Gdy każda kopia zostanie zniszczona, liczba odwołań w oryginalnym obiekcie jest zmniejszana. Oryginalny `CString` obiekt nie jest niszczony, dopóki jego liczba odwołań nie zostanie zredukowana do zera.

`CString`Aby wyłączyć lub włączyć zliczanie odwołań, można użyć funkcji elementów członkowskich [CSimpleStringT:: LockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) i [CSimpleStringT:: UnlockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) .

## <a name="see-also"></a>Zobacz także

[Ogólne tematy dotyczące MFC](../mfc/general-mfc-topics.md)
