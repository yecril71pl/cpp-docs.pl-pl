---
title: Unicode i Multibyte Character Set (MBCS) pomocy technicznej | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 1/09/2017
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], character set support
- MBCS [C++], strings and MFC support
- strings [C++], MBCS support in MFC
- character sets [C++], multibyte
- Unicode [C++], MFC strings
- Unicode [C++], string objects
- strings [C++], Unicode
- strings [C++], character set support
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 74f1f0f88828b5d6355c692aa8eaeecd5869bf57
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43202937"
---
# <a name="unicode-and-multibyte-character-set-mbcs-support"></a>Unicode i Multibyte Character Set (MBCS) pomocy technicznej

Niektóre języki, na przykład w języku japońskim i chińskim, są dużych zestawach znaków. Aby włączyć obsługę programowania dla tych rynkach, biblioteki Microsoft Foundation Class (MFC) umożliwia dwa różne podejścia do obsługi dużych zestawów:

- [Unicode](#mfc-support-for-unicode-strings), `wchar_t` na podstawie szerokości, znaki oraz ciągi zakodowane w formacie UTF-16.

- [Zestawy znaków wielobajtowych (MBCS)](#mfc-support-for-mbcs-strings), **char** oparte na jednym lub znaków dwubajtowych znaków i ciągi zakodowane w zestawie znaków specyficznych dla ustawień regionalnych.

Biblioteki MFC Unicode dla wszystkich nowych wdrożeń ma zalecanymi przez firmę Microsoft i bibliotek MBCS zostały uznane za przestarzałe w programie Visual Studio 2013 i Visual Studio 2015. Obecnie taka ewentualność nie zachodzi. Ostrzeżeń dotyczących zakończenia obsługi MBCS zostały usunięte w programie Visual Studio 2017.

## <a name="mfc-support-for-unicode-strings"></a>Obsługa MFC dla ciągów Unicode

Całej biblioteki klas MFC warunkowo jest włączona dla znaków Unicode i ciągi przechowywane w znaków dwubajtowych w formacie UTF-16. W szczególności klasy [CString](../atl-mfc-shared/reference/cstringt-class.md) ma włączoną obsługę standardu Unicode.

Te biblioteki, debuger i pliki DLL są używane do obsługi standardu Unicode w MFC:

|||||
|-|-|-|-|
|UAFXCW.LIB|UAFXCW. PLIK PDB|UAFXCWD.LIB|UAFXCWD. PLIK PDB|
|MFC*wersji*U.LIB|MFC*wersji*U.PDB|MFC*wersji*U.DLL|MFC*wersji*UD. LIB|
|MFC*wersji*UD. PLIK PDB|MFC*wersji*UD. BIBLIOTEKI DLL|MFCS*wersji*U.LIB|MFCS*wersji*U.PDB|
|MFCS*wersji*UD. LIB|MFCS*wersji*UD. PLIK PDB|MFCM*wersji*U.LIB|MFCM*wersji*U.PDB|
|MFCM*wersji*U.DLL|MFCM*wersji*UD. LIB|MFCM*wersji*UD. PLIK PDB|MFCM*wersji*UD. BIBLIOTEKI DLL|

(*wersji* reprezentuje numer wersji pliku na przykład "140" oznacza, że w wersji 14.0.)

`CString` opiera się na typie danych TCHAR. Jeśli nie zdefiniowano _UNICODE symboli dla kompilacji programu, TCHAR jest zdefiniowana jako typ `wchar_t`, znak 16-bitowych, typ kodowania. W przeciwnym razie TCHAR jest zdefiniowany jako **char**, kodowanie normalne znaki 8-bitowych. W związku z tym, w formacie Unicode `CString` składa się z 16-bitowych znaków. Bez Unicode, składa się z znaki typu **char**.

Na zakończenie programowania Unicode aplikacji, musisz mieć również:

- Użyj makro _T warunkowo ciągi literałowe kod będzie działał Unicode.

- Podczas przekazywania ciągów należy zwrócić uwagę, czy argumenty funkcji wymaga długość w znakach lub długość w bajtach. Różnica jest ważna, jeśli używasz ciągów Unicode.

- Użyj przenośne wersje funkcji obsługi ciągów środowiska wykonawczego języka C.

- Użyj następujących typów danych do znaków i znaków wskaźników:

   - Użyj TCHAR, w której można zastosować **char**.

   - Użyj LPTSTR użycia **char**<strong>\*</strong>.

   - Użyj LPCTSTR użycia **const char**<strong>\*</strong>. `CString` zawiera operator LPCTSTR do konwersji między `CString` i LPCTSTR.

`CString` dostarcza również obsługujących Unicode konstruktorów, operatory przypisania i operatory porównania.

[Odwołanie do biblioteki wykonawczej](../c-runtime-library/c-run-time-library-reference.md) definiuje przenośne wersje wszystkich funkcji obsługi ciągów. Aby uzyskać więcej informacji, zobacz kategorii [internacjonalizacji](../c-runtime-library/internationalization.md).

## <a name="mfc-support-for-mbcs-strings"></a>Obsługa MFC MBCS ciągów

Biblioteka klas jest także włączona dla zestawów znaków wielobajtowych, ale tylko dla znaków dwubajtowych ustawia (DBCS).

W zestawie znaków wielobajtowych znak może być jeden lub dwa bajty szerokości. Jeśli dwa bajty szerokie, jego pierwszy bajt jest specjalny "bajt" oznacza to wybrane z określonego zakresu, w zależności od tego, który kod strony jest używana. Razem wzięte, potencjalny klient, a następnie "Historia bajtów" Określ kodowanie znaków unikatowy.

Jeśli nie zdefiniowano _MBCS symboli dla kompilacji programu, wpisz TCHAR, na którym `CString` jest oparta, mapuje **char**. To pozwala określić, które bajtów w `CString` są wiodące bajty, które są bajtów dziennika. Biblioteki wykonawczej C dostarcza funkcje ułatwiające to.

W obszarze znaków Dwubajtowych podany ciąg może zawierać wszystkie jednobajtowe znaki ANSI, wszystkie znaki dwubajtowe lub połączenie tych dwóch. Te możliwości wymagają szczególną ostrożność podczas analizowania ciągów. Obejmuje to `CString` obiektów.

> [!NOTE]
> Serializacja ciąg Unicode w MFC mogą odczytywać ciągów Unicode i MBCS — niezależnie od tego, która wersja aplikacji, które są uruchomione. Pliki danych można przenosić między Unicode i MBCS wersji programu.

`CString` Użyj funkcji elementów członkowskich specjalne "ogólnego text" wersje funkcji wykonawczej języka C, które wywołują lub używają funkcji obsługujących Unicode. W związku z tym, na przykład jeśli `CString` zazwyczaj wywoływałby funkcję `strcmp`, wywołuje odpowiedniego funkcja generic tekst `_tcscmp` zamiast tego. W zależności od tego, jak zdefiniowano _UNICODE i _MBCS symboli programu `_tcscmp` map w następujący sposób:

|||
|-|-|
|_MBCS zdefiniowano|`_mbscmp`|
|_UNICODE zdefiniowano|`wcscmp`|
|Żadna symbolu zdefiniowanego|`strcmp`|

> [!NOTE]
> _UNICODE i _MBCS symboli programu wzajemnie się wykluczają.

Mapowania zwykłego tekstu, funkcja wszystkie procedury obsługi ciągów czasu wykonywania są omówione w [odwołanie do biblioteki wykonawczej C](../c-runtime-library/c-run-time-library-reference.md). Aby uzyskać listę, zobacz [internacjonalizacji](../c-runtime-library/internationalization.md).

Podobnie `CString` metody są implementowane za pomocą mapowania typów danych typu ogólnego. Umożliwia Unicode i MBCS MFC wykorzystuje TCHAR dla **char** lub `wchar_t`, LPTSTR dla **char** <strong>\*</strong> lub `wchar_t*`i LPCTSTR dla **const char** <strong>\*</strong> lub `const wchar_t*`. Te zapewnienia poprawnego mapowania MBCS lub Unicode.

## <a name="see-also"></a>Zobacz też

[Ciągi (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)  
[Manipulowanie ciągami](../c-runtime-library/string-manipulation-crt.md)  
