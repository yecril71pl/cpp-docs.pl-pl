---
title: Zarządzanie danymi ciągów
ms.date: 11/04/2016
helpviewer_keywords:
- Unicode, string objects
ms.assetid: 0b53a542-eeb1-4108-9ada-6700645b6f8f
ms.openlocfilehash: 7f92b38ac659faef2dd9319b2f204ba837f0d473
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317462"
---
# <a name="string-data-management"></a>Zarządzanie danymi ciągów

Visual C++ udostępnia kilka sposobów zarządzania danymi ciągu:

- [Manipulacja ciągami](../c-runtime-library/string-manipulation-crt.md) do pracy z ciągami zerowymi zakończonymi w stylu C

- Funkcje interfejsu API systemu Win32 do zarządzania ciągami

- Klasa MFC [CStringT Class](../atl-mfc-shared/reference/cstringt-class.md), która zapewnia elastyczne obiekty ciągów o zmiennym rozmiarze

- Klasa [CStringT ,](../atl-mfc-shared/reference/cstringt-class.md)która zapewnia obiekt ciągu niezależnego od MFC z taką samą funkcjonalnością jak`CString`

Prawie wszystkie programy działają z danymi ciągu. `CString` Klasa MFC jest często najlepszym rozwiązaniem dla elastycznej obsługi ciągów. Począwszy od wersji 7.0, `CString` może być używany w programach MFC lub MFC niezależnych. Zarówno biblioteka wykonywania, `CString` jak i ciągi obsługi zawierające znaki wielobajtowe (szerokie), jak w programowaniu Unicode lub MBCS.

W tym artykule opisano usługi ogólnego przeznaczenia, które biblioteka klas zapewnia związane z manipulowania ciągami. Tematy omówione w tym artykule obejmują:

- [Unicode i MBCS Zapewniaj przenośność](#_core_unicode_and_mbcs_provide_portability)

- [CStrings i const char wskaźniki](#_core_cstrings_and_const_char_pointers)

- [Zliczanie odwołań CString](#_core_cstring_reference_counting)

Klasa [CStringT](../atl-mfc-shared/reference/cstringt-class.md) zapewnia obsługę manipulowania ciągami. Jest przeznaczony do zastąpienia i rozszerzenia funkcji normalnie dostarczanych przez pakiet ciągu biblioteki wykonywania języka C. Klasa `CString` dostarcza funkcje członkowskie i operatory dla uproszczonej obsługi ciągów, podobne do tych znalezionych w basic. Klasa zapewnia również konstruktorów i operatorów do `CString`konstruowania, przypisywania i porównywania s i standardowych typów danych ciągów C++. Ponieważ `CString` nie pochodzi `CObject`z programu `CString` , można używać obiektów niezależnie od większości biblioteki klas programu Microsoft Foundation (MFC).

`CString`obiekty podążają za "semantyki wartości". Obiekt `CString` reprezentuje unikatową wartość. Pomyśl o `CString` jako rzeczywisty ciąg, a nie jako wskaźnik do ciągu.

Obiekt `CString` reprezentuje sekwencję zmiennej liczby znaków. `CString`obiekty mogą być traktowane jako tablice znaków.

## <a name="unicode-and-mbcs-provide-portability"></a><a name="_core_unicode_and_mbcs_provide_portability"></a>Unicode i MBCS zapewniają przenośność

W wersji MFC 3.0 i nowszej MFC, w tym `CString`, jest włączona zarówno dla unicode i wielobajtowych zestawów znaków (MBCS). Ta obsługa ułatwia pisanie aplikacji przenośnych, które można tworzyć dla znaków Unicode lub ANSI. Aby włączyć tę przenośność, `CString` każdy znak w obiekcie jest typu `wchar_t` TCHAR, który jest zdefiniowany tak, jak `char` w przypadku definiowania symbolu _UNICODE podczas tworzenia aplikacji lub tak, jakby nie. Znak `wchar_t` ma 16 bitów szerokości. MBCS jest włączona, jeśli tworzysz z symbolem _MBCS zdefiniowany. Sam MFC jest zbudowany z symbolem _MBCS (dla bibliotek NAFX) lub zdefiniowanym symbolem _UNICODE (dla bibliotek UAFX).

> [!NOTE]
> Przykłady `CString` w tym i towarzyszących artykułów na ciągi pokazują dosłowne ciągi poprawnie sformatowane dla przenoszenia Unicode, przy użyciu _T makra, który tłumaczy ciąg literał do formularza:

`L"literal string"`

> [!NOTE]
> kompilator traktuje jako ciąg Unicode. Na przykład następujący kod:

[!code-cpp[NVC_ATLMFC_Utilities#187](../atl-mfc-shared/codesnippet/cpp/string-data-management_1.cpp)]

> [!NOTE]
> jest tłumaczony jako ciąg Unicode, jeśli _UNICODE jest zdefiniowany lub jako ciąg ANSI, jeśli nie. Aby uzyskać więcej informacji, zobacz artykuł [Obsługa unicode i wielobajtowego zestawu znaków (MBCS).](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)

Obiekt `CString` może przechowywać do INT_MAX (2 147 483 647) znaków. Typ danych TCHAR służy do uzyskania lub `CString` ustawić poszczególne znaki wewnątrz obiektu. W przeciwieństwie do `CString` tablic znakowych klasa ma wbudowaną funkcję alokacji pamięci. Dzięki `CString` temu obiekty mogą automatycznie rosnąć w razie potrzeby (oznacza to, że nie musisz się martwić o powiększanie `CString` obiektu, aby zmieścić dłuższe ciągi).

## <a name="cstrings-and-const-char-pointers"></a><a name="_core_cstrings_and_const_char_pointers"></a>CStrings i const char wskaźniki

Obiekt `CString` może również działać jak literał ciąg `PCXSTR`w stylu C (, który jest taki sam jak **const char,** <strong>\*</strong> jeśli nie w Unicode). Operator konwersji [CSimpleStringT::operator PCXSTR](../atl-mfc-shared/reference/csimplestringt-class.md#operator_pcxstr) umożliwia `CString` swobodne zastępowanie obiektów wskaźnikami znaków w wywołaniach funkcji. Konstruktor **CString( LPCWSTR)** `pszSrc` **)** umożliwia zastępowanie wskaźników `CString` znaków obiektami.

Nie podejmowana jest `CString` żadna próba składania obiektów. Jeśli na `CString` przykład zostaną `Chicago`wprowadzone dwa obiekty `Chicago` zawierające , na przykład, znaki są przechowywane w dwóch miejscach. (To może nie być prawdziwe przyszłych wersji MFC, więc nie należy od niego zależeć.)

> [!NOTE]
> Użyj [CSimpleStringT::GetBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) i [CSimpleStringT::ReleaseBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer) funkcji członkowskich, gdy `CString` trzeba bezpośrednio uzyskać dostęp jako wskaźnik niestałe do znaku.

> [!NOTE]
> Użyj [CStringT::AllocSysString](../atl-mfc-shared/reference/cstringt-class.md#allocsysstring) i [CStringT::SetSysString](../atl-mfc-shared/reference/cstringt-class.md#setsysstring) funkcji członkowskich do przydzielania i ustawiania obiektów BSTR używanych w automatyzacji (dawniej znany jako automatyzacji OLE).

> [!NOTE]
> Jeśli to `CString` możliwe, przydzielić obiekty na ramce, a nie na stercie. Oszczędza to pamięć i upraszcza przekazywanie parametrów.

Klasa `CString` nie jest implementowana jako klasa kolekcji `CString` biblioteki klas Programu Microsoft Foundation, chociaż obiekty z pewnością mogą być przechowywane jako elementy w kolekcjach.

## <a name="cstring-reference-counting"></a><a name="_core_cstring_reference_counting"></a>Zliczanie odwołań CString

Od wersji MFC 4.0, gdy [CStringT Class](../atl-mfc-shared/reference/cstringt-class.md) obiekty są kopiowane, MFC zwiększa liczbę odwołań, a nie kopiowanie danych. Dzięki temu przekazywanie parametrów `CString` przez wartość i zwracanie obiektów według wartości jest bardziej wydajne. Te operacje powodują konstruktora kopii do wywołania, czasami więcej niż jeden raz. Zwiększenie liczby odwołań zmniejsza obciążenie dla tych typowych `CString` operacji i sprawia, że przy użyciu bardziej atrakcyjną opcję.

Jak każda kopia jest niszczony, liczba odwołań w oryginalnym obiekcie jest zmniejszana. Oryginalny `CString` obiekt nie jest niszczony, dopóki jego liczba odwołań nie zostanie zmniejszona do zera.

Można użyć `CString` funkcji członkowskich [CSimpleStringT::LockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) i [CSimpleStringT::UnlockBuffer,](../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) aby wyłączyć lub włączyć zliczanie odwołań.

## <a name="see-also"></a>Zobacz też

[Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)
