---
title: Zarządzanie danymi ciągu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Unicode, string objects
ms.assetid: 0b53a542-eeb1-4108-9ada-6700645b6f8f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: acf14ebec5417179a94d0a6ffefdb473966f0c2e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="string-data-management"></a>Zarządzanie danymi ciągu
Visual C++ zapewnia wiele sposobów zarządzać danymi ciągu:  
  
-   [Ciąg manipulowania](../c-runtime-library/string-manipulation-crt.md) do pracy z ciągi zakończone wartością null w stylu języka C  
  
-   Funkcje interfejsu API Win32 zarządzania ciągów  
  
-   Klasy MFC [CStringT klasy](../atl-mfc-shared/reference/cstringt-class.md), zapewniający elastyczne, o zmiennym rozmiarze ciągu obiektów  
  
-   Klasa [CStringT klasy](../atl-mfc-shared/reference/cstringt-class.md), co umożliwia obiektu ciąg MFC z funkcji `CString`  
  
 Prawie wszystkie programy pracować z danymi ciągu. MFC `CString` klasy często najlepszym rozwiązaniem jest obsługi elastyczne ciągu. Począwszy od wersji 7.0, `CString` mogą być używane w MFC lub niezależny od MFC programów. Biblioteki wykonawcze i `CString` obsługuje ciągi zawierające znaki wielobajtowe (szeroka), tak jak programowania Unicode i MBCS.  
  
 W tym artykule opisano usługi programu ogólnego przeznaczenia, które udostępnia biblioteki klas związanych z manipulowanie ciągami. Omówione w tym artykule tematy obejmują:  
  
-   [Unicode i MBCS Podaj przenośność](#_core_unicode_and_mbcs_provide_portability)  
  
-   [CStrings i const char wskaźników](#_core_cstrings_and_const_char_pointers)  
  
-   [Cstring — zliczanie](#_core_cstring_reference_counting)  
  
 [Klasy CStringT](../atl-mfc-shared/reference/cstringt-class.md) klasy zapewnia obsługę manipulowanie ciągami. Jest on przeznaczony do zastąpienia i rozszerzyć funkcjonalność zwykle pakietu ciąg biblioteki wykonawczej języka C. `CString` Klasa zapewnia funkcje Członkowskie i operatory ciąg uproszczone Obsługa, podobne do tych znaleziono Basic. Ta klasa dostarcza również konstruktory i operatory do tworzenia, przypisywania i porównywanie **CStrings** i standardowe typy danych ciąg języka C++. Ponieważ `CString` nie pochodzi od `CObject`, można użyć `CString` obiektów niezależnie od najbardziej Microsoft Foundation Class biblioteki (MFC).  
  
 `CString` obiekty wykonaj "wartość semantyki". A `CString` obiekt reprezentuje unikatową wartość. Pomyśl o `CString` jako rzeczywisty ciąg, a nie jako wskaźnik do ciągu.  
  
 A `CString` obiekt reprezentuje sekwencję zmienną liczbę znaków. `CString` obiekty mogą być uważane za tablice znaków.  
  
##  <a name="_core_unicode_and_mbcs_provide_portability"></a> Unicode i MBCS zapewniają przenośność  
 Z tym w wersji 3.0 lub nowszej, MFC, MFC `CString`, jest włączone dla zestawów znaków wielobajtowych (MBCS) i Unicode. Ta obsługa ułatwia pisanie aplikacji przenośnych można tworzyć dla znaków Unicode lub ANSI. Aby włączyć ten przenośność każdego znaku w `CString` obiekt jest typu **tchar —**, która została zdefiniowana jako `wchar_t` w przypadku definiowania symbol **_unicode —** podczas kompilowania aplikacji lub jako `char` , jeśli nie. A `wchar_t` znak jest szeroki 16 bitów. MBCS jest włączona, jeśli kompilacji z symbolem **_MBCS** zdefiniowane. MFC sam jest utworzony przy użyciu jednej **_MBCS** symbolu (w przypadku bibliotek NAFX) lub **_unicode —** symbolu (w przypadku bibliotek UAFX) zdefiniowane.  
  
> [!NOTE]
>  `CString` Przykłady w tym i towarzyszące artykuły Pokaż ciągi literałów ciągów poprawnie sformatowana przenośności Unicode, za pomocą **_t —** makra, który tłumaczy literału ciągu do formularza:  
  
 `L"literal string"`  
  
> [!NOTE]
>  które kompilator traktuje jako ciąg Unicode. Na przykład następujący kod:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#187](../atl-mfc-shared/codesnippet/cpp/string-data-management_1.cpp)]  
  
> [!NOTE]
>  przetłumaczono jako ciąg znaków Unicode, jeśli **_unicode —** zdefiniowano lub jako ANSI string, jeśli nie. Aby uzyskać więcej informacji, zobacz artykuł [Unicode i pomocy technicznej ustawić znaków wielobajtowych (MBCS)](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md).  
  
 A `CString` obiekt może przechowywać maksymalnie **int_max —** znaków (2 147 483 647). **Tchar —** — typ danych jest używany do pobierania lub ustawiania znaki wewnątrz `CString` obiektu. W odróżnieniu od tablice znaków `CString` klasa ma możliwość alokacji pamięci wbudowanych. Dzięki temu `CString` obiektów do automatycznej zmiany rozmiaru w razie potrzeby (to znaczy, nie trzeba martwić rośnie `CString` obiektu do ciągów dłużej).  
  
##  <a name="_core_cstrings_and_const_char_pointers"></a> CStrings i const char wskaźników  
 A `CString` obiektu mogą również działać tak jak literał ciągu w stylu języka C ( `PCXSTR`, która jest taka sama jak **const char\***  if pod Unicode nie). [CSimpleStringT::operator PCXSTR](../atl-mfc-shared/reference/csimplestringt-class.md#operator_pcxstr) operatora konwersji umożliwia `CString` obiektów można swobodnie podstawić wskaźniki znak w wywołaniach funkcji. **Cstring — (LPCWSTR** `pszSrc` **)** Konstruktor umożliwia wskaźniki znaków do zastąpienia dla `CString` obiektów.  
  
 Nie są podejmowane próby się `CString` obiektów. Jeśli dwa `CString` obiektów zawierających `Chicago`, na przykład znaki w `Chicago` są przechowywane w dwóch miejscach. (To nie będzie istotne w przyszłych wersjach MFC, więc należy nie zależą od niej.)  
  
> [!NOTE]
>  Użyj [CSimpleStringT::GetBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) i [CSimpleStringT::ReleaseBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer) funkcje Członkowskie, gdy trzeba uzyskać bezpośredni dostęp do `CString` jako nieunikatowego wskaźnik do znaku.  
  
> [!NOTE]
>  Użyj [CStringT::AllocSysString](../atl-mfc-shared/reference/cstringt-class.md#allocsysstring) i [CStringT::SetSysString](../atl-mfc-shared/reference/cstringt-class.md#setsysstring) funkcje Członkowskie można przydzielić i ustawić `BSTR` obiektów używanych w automatyzacji (wcześniej znane jako automatyzacji OLE).  
  
> [!NOTE]
>  Jeśli to możliwe, przydziel `CString` obiektów w ramce, a nie na stosie. To oszczędzić pamięć i upraszcza przekazywanie parametru.  
  
 `CString` Klasy nie jest zaimplementowana jako Klasa kolekcji Microsoft Foundation Class Library, mimo że `CString` obiekty mogą być przechowywane na pewno jako elementy w kolekcji.  
  
##  <a name="_core_cstring_reference_counting"></a> Cstring — zliczanie  
 Począwszy od wersji 4.0, MFC podczas [klasy CStringT](../atl-mfc-shared/reference/cstringt-class.md) obiekty są kopiowane, MFC zwiększa liczbę odwołań zamiast kopiowania danych. Dzięki temu przekazywanie parametrów według wartości i zwracanie `CString` obiektów przez wartość większą wydajność. Te operacje powodują Konstruktor kopiujący jest wywoływana czasami więcej niż raz. Zwiększanie liczby odwołanie zmniejsza obciążenie związane z tym te typowych operacji i sprawia, że przy użyciu `CString` atrakcyjniejsze opcji.  
  
 Jak każdej kopii zostanie zniszczony, liczba odwołań w oryginalnym obiektu jest zmniejszany. Oryginalna `CString` obiektu nie jest niszczony, dopóki licznika jego odwołań jest mniejsze od zera.  
  
 Można użyć `CString` funkcje Członkowskie [CSimpleStringT::LockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) i [CSimpleStringT::UnlockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) można wyłączyć lub włączyć liczenie odwołań.  
  
## <a name="see-also"></a>Zobacz też  
 [Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)

