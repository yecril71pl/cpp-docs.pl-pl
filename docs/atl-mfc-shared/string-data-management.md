---
title: Ciąg zarządzanie danymi | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: b4e82671973f2d841c6c0797fb73ad582ce203f1
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43214350"
---
# <a name="string-data-management"></a>Zarządzanie danymi ciągów
Visual C++ oferuje kilka sposobów, aby zarządzać danymi ciąg:  
  
-   [Ciąg manipulowania](../c-runtime-library/string-manipulation-crt.md) do pracy z ciągami znaków zakończony znakiem null w stylu języka C  
  
-   Funkcji Win32 API do zarządzania ciągów  
  
-   Klasy MFC [CStringT, klasa](../atl-mfc-shared/reference/cstringt-class.md), który zapewnia elastyczne ciąg o zmiennym rozmiarze obiektów  
  
-   Klasa [CStringT, klasa](../atl-mfc-shared/reference/cstringt-class.md), co umożliwia niezależne od MFC obiekt ciągu z taką samą funkcjonalność jak `CString`  
  
 Niemal we wszystkich programach pracować z danymi ciągu. Biblioteki MFC `CString` klasy często najlepszym rozwiązaniem jest obsługi elastyczne ciągu. Począwszy od wersji 7.0, `CString` mogą być używane w programy MFC lub niezależne od MFC. Biblioteka środowiska uruchomieniowego i `CString` obsługują ciągi zawierające znaki wielobajtowe (rozległych), tak jak w Unicode i MBCS programowania.  
  
 W tym artykule opisano usług ogólnego przeznaczenia, udostępnianych przez bibliotekę klas powiązanych do manipulowania ciągami. Tematy omówione w tym artykule obejmują:  
  
-   [Unicode i MBCS — zapewnia przenośność](#_core_unicode_and_mbcs_provide_portability)  
  
-   [CStrings i const char wskaźników](#_core_cstrings_and_const_char_pointers)  
  
-   [Zliczanie odwołań CString](#_core_cstring_reference_counting)  
  
 [CStringT, klasa](../atl-mfc-shared/reference/cstringt-class.md) klasy zapewnia obsługę manipulowania ciągami. Jest on przeznaczony do zastąpienia i Rozszerz funkcje zwykle zapewniane przez pakiet parametrów biblioteki wykonawczej C. `CString` Klasy dostarcza funkcji elementów członkowskich i operatory Obsługa parametry uproszczone, podobne do tych w Basic. Ta klasa oferuje również operatory i konstruktory dla tworzenia, przypisywania i porównywanie `CString`s i standard C++ ciąg typów danych. Ponieważ `CString` nie pochodzi od `CObject`, możesz użyć `CString` obiektów, niezależnie od najbardziej Microsoft Foundation Class Library (MFC).  
  
 `CString` Postępuj zgodnie z obiektów, "wartość semantyki." A `CString` obiekt reprezentuje unikatową wartość. Traktować `CString` jako rzeczywisty ciąg, a nie jako wskaźnik do ciągu.  
  
 A `CString` obiekt reprezentuje sekwencję zmienną liczbę znaków. `CString` obiekty mogą być uważane za tablice znaków.  
  
##  <a name="_core_unicode_and_mbcs_provide_portability"></a> Unicode i MBCS zapewnia przenośność  
 Za pomocą MFC w wersji 3.0 i nowszych, MFC, w tym `CString`, włączono obsługę standardu Unicode i zestawach znaków wielobajtowych (MBCS). Ta funkcja ułatwia pisać aplikacje przenośne, którego można tworzyć dla znaków Unicode lub ANSI. Aby umożliwić tej przenośności możesz każdego znaku w `CString` TCHAR, która jest zdefiniowana jako typ obiektu to `wchar_t` po zdefiniowaniu _UNICODE symboli podczas kompilacji aplikacji lub jako `char` w przeciwnym razie. A `wchar_t` znak jest 16 bitów szerokości. MBCS jest włączona, jeśli kompilujesz z _MBCS symbol zdefiniowany. MFC sam został utworzony za pomocą symbolu _MBCS (dla biblioteki NAFX) lub symbol _UNICODE (dla biblioteki UAFX) zdefiniowany.  
  
> [!NOTE]
>  `CString` w tym i towarzyszące artykułów na ciągi przykładach ciągi literałowe poprawnie sformatowana przenośności Unicode, użycie makra _T, co przekłada się ciągiem literału formularza:  
  
 `L"literal string"`  
  
> [!NOTE]
>  które kompilator traktuje jako ciąg Unicode. Na przykład poniższy kod:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#187](../atl-mfc-shared/codesnippet/cpp/string-data-management_1.cpp)]  
  
> [!NOTE]
>  jest tłumaczony jako ciąg Unicode, jeśli nie zdefiniowano _UNICODE lub na ciąg ANSI, w przeciwnym razie. Aby uzyskać więcej informacji, zobacz artykuł [Obsługa zestawu znaków wielobajtowych (MBCS) i Unicode](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md).  
  
 Element `CString` obiektu można przechowywać w znaków INT_MAX (2 147 483 647). Tchar — typ danych służy do pobierania lub ustawiania pojedynczych znaków wewnątrz `CString` obiektu. W odróżnieniu od tablic znaków `CString` klasy zawiera funkcję alokacji pamięci wbudowane. Dzięki temu `CString` obiektów, aby automatycznie zwiększać stosownie do potrzeb (oznacza to, że nie masz już martwić się o rosnący `CString` obiektu do ciągów dłuższe).  
  
##  <a name="_core_cstrings_and_const_char_pointers"></a> CStrings i const char wskaźników  
 A `CString` obiektu również może zachowywać się jak ciąg literału stylu języka C ( `PCXSTR`, która jest taka sama jak **const char** <strong>\*</strong> if nieobjętego Unicode). [CSimpleStringT::operator PCXSTR](../atl-mfc-shared/reference/csimplestringt-class.md#operator_pcxstr) umożliwia operatora konwersji `CString` obiektów można swobodnie zamieniony na znak wskaźników w wywołaniach funkcji. **CString (LPCWSTR** `pszSrc` **)** Konstruktor pozwala znak wskaźników do podstawienia pod `CString` obiektów.  
  
 Aby złożyć jest podejmowana próba `CString` obiektów. Jeśli wprowadzisz dwa `CString` obiektów zawierających `Chicago`, na przykład znaki w `Chicago` są przechowywane w dwóch miejscach. (To nie będzie true dla przyszłych wersji MFC, więc należy nie zależą od niej.)  
  
> [!NOTE]
>  Użyj [CSimpleStringT::GetBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) i [CSimpleStringT::ReleaseBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer) funkcje Członkowskie, gdy trzeba uzyskać bezpośredni dostęp do `CString` jako stałymi wskaźnik do znaku.  
  
> [!NOTE]
>  Użyj [CStringT::AllocSysString](../atl-mfc-shared/reference/cstringt-class.md#allocsysstring) i [CStringT::SetSysString](../atl-mfc-shared/reference/cstringt-class.md#setsysstring) funkcji elementów członkowskich do przydzielania i ustawienia BSTR obiekty używane w usłudze Automation (wcześniej znane jako automatyzacji OLE).  
  
> [!NOTE]
>  Jeśli to możliwe, przydziel `CString` obiektów na ramce, a nie na stosie. Zużycie pamięci i ułatwia przekazywanie parametru.  
  
 `CString` Klasy nie jest zaimplementowana jako bibliotekę Microsoft Foundation Class klasy kolekcji, chociaż `CString` bez obaw obiekty mogą być przechowywane w postaci elementów w kolekcji.  
  
##  <a name="_core_cstring_reference_counting"></a> Zliczanie odwołań CString  
 Począwszy od wersji 4.0, MFC podczas [CStringT, klasa](../atl-mfc-shared/reference/cstringt-class.md) obiekty są kopiowane, MFC zwiększa licznik odwołań zamiast kopiowania danych. To sprawia, że przekazywanie parametrów przez wartość i zwracanie `CString` obiektów według wartości bardziej wydajne. Te operacje powodują Konstruktor kopiujący jest wywoływana, czasami więcej niż raz. Zwiększenie liczby odwołań zmniejsza obciążenie, że te typowych operacji i sprawia, że za pomocą `CString` bardziej atrakcyjne opcji.  
  
 Ponieważ każda kopia jest niszczony, licznik odwołań w oryginalnym obiekcie zostanie zmniejszona. Oryginalny `CString` obiekt nie jest niszczony, dopóki jego licznik odwołań jest mniejsze od zera.  
  
 Możesz użyć `CString` elementów członkowskich [CSimpleStringT::LockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) i [CSimpleStringT::UnlockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) wyłączyć lub włączyć zliczanie odwołań.  
  
## <a name="see-also"></a>Zobacz też  
 [Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)

