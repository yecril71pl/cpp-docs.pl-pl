---
title: Obsługa zestawu znaków Unicode i wielobajtowego (MBCS)
ms.date: 01/09/2017
helpviewer_keywords:
- MFC [C++], character set support
- MBCS [C++], strings and MFC support
- strings [C++], MBCS support in MFC
- character sets [C++], multibyte
- Unicode [C++], MFC strings
- Unicode [C++], string objects
- strings [C++], Unicode
- strings [C++], character set support
ms.openlocfilehash: 217690e09ed595bb9fa9572693bf774259c42412
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219030"
---
# <a name="unicode-and-multibyte-character-set-mbcs-support"></a>Obsługa zestawu znaków Unicode i wielobajtowego (MBCS)

Niektóre języki, na przykład japoński i chiński, mają duże zestawy znaków. Aby obsługiwać Programowanie dla tych rynków, biblioteka MFC (MFC) oferuje dwa różne podejścia do obsługi dużych zestawów znaków:

- [Unicode](#mfc-support-for-unicode-strings), w **`wchar_t`** oparciu o szerokie znaki i ciągi zakodowane jako UTF-16.

- [Zestawy znaków wielobajtowych (MBCS)](#mfc-support-for-mbcs-strings), **`char`** znaki pojedynczego lub dwubajtowego i ciągi zakodowane w zestawie znaków specyficznych dla ustawień regionalnych.

Firma Microsoft zaleca biblioteki Unicode MFC do wszystkich nowych wdrożeń, a biblioteki MBCS były przestarzałe w Visual Studio 2013 i Visual Studio 2015. Obecnie taka ewentualność nie zachodzi. Ostrzeżenia o zaniechaniu MBCS zostały usunięte w programie Visual Studio 2017.

## <a name="mfc-support-for-unicode-strings"></a>Obsługa MFC dla ciągów Unicode

Cała biblioteka klas MFC jest warunkowo włączona dla znaków Unicode i ciągów przechowywanych w postaci znaków dwubajtowych w formacie UTF-16. W szczególności Klasa [CString](../atl-mfc-shared/reference/cstringt-class.md) jest włączona w formacie Unicode.

Te biblioteki, debugery i pliki DLL są używane do obsługi standardu Unicode w MFC:

|||||
|-|-|-|-|
|UAFXCW. LIB|UAFXCW. PDB|UAFXCWD. LIB|UAFXCWD. PDB|
|MFC*wersja*U. lib|*Wersja*pliku U. pdb usługi MFC|*Wersja* MFCU.DLL|*Wersja*MFC ud. LIB|
|*Wersja*MFC ud. PDB|*Wersja* MFCUD.DLL|MFCS*wersja*U. lib|MFCS*wersja*U. pdb|
|MFCS*wersja*ud. LIB|MFCS*wersja*ud. PDB|MFCM*wersja*U. lib|MFCM*wersja*U. pdb|
|*Wersja* MFCMU.DLL|MFCM*wersja*ud. LIB|MFCM*wersja*ud. PDB|*Wersja* MFCMUD.DLL|

(*wersja* reprezentuje numer wersji pliku, na przykład "140" oznacza wersję 14,0).

`CString`jest oparty na typie danych używanie TCHAR. Jeśli symbol _UNICODE jest zdefiniowany dla kompilacji programu, używanie TCHAR jest zdefiniowany jako typ **`wchar_t`** , 16-bitowy typ kodowania znaków. W przeciwnym razie używanie TCHAR jest zdefiniowane jako **`char`** , normalne 8-bitowe kodowanie znaków. W związku z tym, w formacie Unicode, `CString` składa się z 16-bitowych znaków. Bez Unicode, składa się z znaków typu **`char`** .

Aby zakończyć programowanie w formacie Unicode aplikacji, należy również:

- Użyj makra _T, aby warunkowo zdekodować ciągi literałów, które mają być przenośne w formacie Unicode.

- W przypadku przekazywania ciągów należy zwrócić uwagę, czy argumenty funkcji wymagają długości w znakach lub długości w bajtach. Różnica jest ważna, jeśli używasz ciągów Unicode.

- Używaj przenośnych wersji funkcji obsługi ciągów czasu wykonywania języka C.

- Używaj następujących typów danych dla znaków i wskaźników znaków:

  - Użyj używanie TCHAR, gdzie chcesz użyć **`char`** .

  - Użyj LPTSTR, gdzie chcesz użyć **`char`** <strong>\*</strong> .

  - Użyj LPCTSTR, gdzie używać **znaku const** <strong>\*</strong> . `CString`zapewnia operatorowi LPCTSTR konwersję między `CString` i LPCTSTR.

`CString`dostarcza także konstruktory obsługujące kod Unicode, operatory przypisania i operatory porównania.

[Dokumentacja biblioteki wykonawczej](../c-runtime-library/c-run-time-library-reference.md) definiuje przenośne wersje wszystkich funkcji obsługi ciągów. Aby uzyskać więcej informacji, zapoznaj się [z kategorią](../c-runtime-library/internationalization.md).

## <a name="mfc-support-for-mbcs-strings"></a>Obsługa MFC dla ciągów MBCS

Biblioteka klas jest również włączona dla zestawów znaków wielobajtowych, ale tylko w przypadku zestawów znaków dwubajtowych (DBCS).

W zestawie znaków wielobajtowych znak może być jeden lub dwa bajty. Jeśli jest to dwa bajty, jego pierwszy bajt jest specjalnym "bajtem wiodącym", który jest wybierany z określonego zakresu, w zależności od tego, która strona kodowa jest używana. Razem, lider i "Trail Bytes" określają unikatowe kodowanie znaków.

Jeśli symbol _MBCS jest zdefiniowany dla kompilacji programu, wpisz używanie TCHAR, na którym `CString` jest oparty, mapuje na **`char`** . Istnieje możliwość określenia, które bajty w `CString` bajtach są potencjalnymi, a które są bajtami końcowymi. Biblioteka wykonawcza C udostępnia funkcje ułatwiające określenie tego.

W obszarze DBCS dany ciąg może zawierać wszystkie jednobajtowe znaki ANSI, wszystkie znaki dwubajtowe lub kombinację dwóch. Te możliwości wymagają specjalnej opieki nad analizowaniem ciągów. Obejmuje to `CString` obiekty.

> [!NOTE]
> Serializacja ciągów Unicode w MFC może odczytywać ciągi Unicode i MBCS, niezależnie od tego, która wersja aplikacji jest uruchomiona. Pliki danych są przenośne między wersjami Unicode i MBCS programu.

`CString`funkcje członkowskie używają specjalnej "ogólnego tekstu" funkcji języka uruchomieniowego C, które wywołuje, lub korzystają z funkcji obsługujących kod Unicode. W związku z tym, na przykład, jeśli `CString` Funkcja zwykle wywołuje `strcmp` , zamiast tego wywoła odpowiednią funkcję tekstu ogólnego `_tcscmp` . W zależności od tego, jak symbole _MBCS i _UNICODE są zdefiniowane, `_tcscmp` mapuje w następujący sposób:

|||
|-|-|
|_MBCS zdefiniowano|`_mbscmp`|
|_UNICODE zdefiniowano|`wcscmp`|
|Nie zdefiniowano symbolu|`strcmp`|

> [!NOTE]
> Symbole _MBCS i _UNICODE wykluczają się wzajemnie.

Mapowania funkcji tekstu ogólnego dla wszystkich procedur obsługi ciągów w czasie wykonywania zostały omówione w temacie [Informacje o bibliotece wykonawczej C](../c-runtime-library/c-run-time-library-reference.md). Aby uzyskać listę, zobacz temat [międzynarodowe](../c-runtime-library/internationalization.md).

Podobnie `CString` metody są implementowane za pomocą ogólnych mapowań typów danych. Aby włączyć zarówno MBCS, jak i Unicode, MFC używa używanie TCHAR dla **`char`** lub **`wchar_t`** , LPTStr dla **`char`** <strong>\*</strong> lub `wchar_t*` , i LPCTSTR dla **const char** <strong>\*</strong> lub `const wchar_t*` . Zapewniają one poprawne mapowania dla MBCS lub Unicode.

## <a name="see-also"></a>Zobacz też

[Ciągi (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[Manipulowanie ciągami](../c-runtime-library/string-manipulation-crt.md)
