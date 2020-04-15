---
title: Obsługa Unicode i Multibyte Character Set (MBCS)
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
ms.openlocfilehash: e1b93a3540cba553afd8f133c18496bddbd561b8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317437"
---
# <a name="unicode-and-multibyte-character-set-mbcs-support"></a>Obsługa Unicode i Multibyte Character Set (MBCS)

Niektóre języki, na przykład japoński i chiński, mają duże zestawy znaków. Aby obsługiwać programowanie dla tych rynków, Biblioteka klas Microsoft Foundation (MFC) umożliwia dwa różne podejścia do obsługi dużych zestawów znaków:

- [Unicode](#mfc-support-for-unicode-strings) `wchar_t` , oparte na szerokich znakach i ciągach zakodowanych jako UTF-16.

- [Wielobajtowe zestawy znaków (MBCS),](#mfc-support-for-mbcs-strings)znaki jedno- lub dwubajtowe i ciągi znaków zakodowane w zestawie znaków specyficznych dla ustawień regionalnych. **char**

Firma Microsoft zaleciła biblioteki MFC Unicode dla wszystkich nowych programów, a biblioteki MBCS zostały przestarzałe w programach Visual Studio 2013 i Visual Studio 2015. Obecnie taka ewentualność nie zachodzi. Ostrzeżenia dotyczące wycofania MBCS zostały usunięte w programie Visual Studio 2017.

## <a name="mfc-support-for-unicode-strings"></a>Obsługa MFC dla ciągów Unicode

Cała biblioteka klas MFC jest warunkowo włączona dla znaków i ciągów Unicode przechowywanych w szerokich znakach jako UTF-16. W szczególności klasa [CString](../atl-mfc-shared/reference/cstringt-class.md) jest unicode włączone.

Te pliki biblioteki, debugera i biblioteki DLL są używane do obsługi unicode w MFC:

|||||
|-|-|-|-|
|UAFXCW. Lib|UAFXCW. Pdb|UAFXCWD. Lib|UAFXCWD. Pdb|
|*Wersja*MFC U.LIB|*Wersja*MFC U.PDB|*Wersja*MFC U.DLL|*Wersja*MFC UD. Lib|
|*Wersja*MFC UD. Pdb|*Wersja*MFC UD. Dll|*Wersja*MFCS U.LIB|*Wersja*MFCS U.PDB|
|*Wersja*MFCS UD. Lib|*Wersja*MFCS UD. Pdb|*Mfcm wersja*U.LIB|*Mfcm wersja*U.PDB|
|*Mfcm wersja*U.DLL|*Wersja*MFCM UD. Lib|*Wersja*MFCM UD. Pdb|*Wersja*MFCM UD. Dll|

*(wersja* reprezentuje numer wersji pliku; na przykład "140" oznacza wersję 14.0.)

`CString`opiera się na typie danych TCHAR. Jeśli symbol _UNICODE jest zdefiniowany dla kompilacji programu, TCHAR `wchar_t`jest zdefiniowany jako typ, typ kodowania znaków 16-bitowych. W przeciwnym razie TCHAR jest zdefiniowany jako **char**, normalne kodowanie znaków 8-bitowych. W związku z tym `CString` w unicode a składa się z 16-bitowych znaków. Bez Unicode składa się ze znaków typu **char**.

Aby ukończyć programowanie aplikacji w standardzie Unicode, należy również:

- Użyj makra _T, aby warunkowo kodować ciągi literału, które mają być przenośne do unicode.

- Podczas przekazywania ciągów należy zwrócić uwagę na to, czy argumenty funkcji wymagają długości znaków, czy długości w bajtach. Różnica jest ważna, jeśli używasz ciągów Unicode.

- Użyj przenośnych wersji funkcji obsługi ciągów w czasie wykonywania języka C.

- Użyj następujących typów danych dla znaków i wskaźników znaków:

  - Użyj TCHAR, gdzie można użyć **char**.

  - Użyj LPTSTR, gdzie można użyć **char**<strong>\*</strong>.

  - Użyj LPCTSTR, gdzie można użyć **const char**<strong>\*</strong>. `CString`zapewnia operatorowi LPCTSTR `CString` konwersję między i LPCTSTR.

`CString`dostarcza również konstruktory obsługujące Unicode, operatory przypisania i operatory porównania.

[Odwołanie do biblioteki w czasie](../c-runtime-library/c-run-time-library-reference.md) wykonywania definiuje przenośne wersje wszystkich jego funkcji obsługi ciągów. Aby uzyskać więcej informacji, zobacz kategorię [Internacjonalizacja](../c-runtime-library/internationalization.md).

## <a name="mfc-support-for-mbcs-strings"></a>Obsługa MFC dla ciągów MBCS

Biblioteka klas jest również włączona dla zestawów znaków wielobajtowych, ale tylko dla zestawów znaków dwubajtowych (DBCS).

W zestawie znaków wielobajtowych znak może mieć jeden lub dwa bajty szerokości. Jeśli jest to dwa bajty szerokości, jego pierwszy bajt jest specjalny "prowadź bajt", który jest wybrany z określonego zakresu, w zależności od tego, która strona kodowa jest w użyciu. Razem wzięte, potencjalny klient i "bajty szlakowe" określają unikatowe kodowanie znaków.

Jeśli symbol _MBCS jest zdefiniowany dla kompilacji programu, wpisz TCHAR, na którym `CString` jest oparty, mapuje na **char**. To do Ciebie, aby określić, `CString` które bajty w są bajtami ołowiu i które są bajtami szlaku. Biblioteka wykonywania języka C dostarcza funkcje ułatwiające określenie tego.

W obszarze DBCS dany ciąg może zawierać wszystkie jedno bajtowe znaki ANSI, wszystkie znaki dwu bajtowe lub kombinację tych dwóch znaków. Możliwości te wymagają szczególnej ostrożności w parsowaniu strun. Obejmuje `CString` to obiekty.

> [!NOTE]
> Serializacja ciągu Unicode w MFC może odczytywać ciągi Unicode i MBCS niezależnie od wersji uruchomionej aplikacji. Pliki danych są przenośne między wersjami Unicode i MBCS programu.

`CString`funkcje członkowskie używają specjalnych wersji "tekstu ogólnego" wywoływanych przez nich funkcji wykonywania języka C lub używają funkcji obsługujących unicode. W związku z tym, `CString` jeśli funkcja `strcmp`zazwyczaj wywołuje , wywołuje odpowiednią `_tcscmp` funkcję tekstu ogólnego zamiast. W zależności od tego, jak zdefiniowane są _MBCS `_tcscmp` i _UNICODE, mapy są następujące:

|||
|-|-|
|_MBCS zdefiniowano|`_mbscmp`|
|_UNICODE zdefiniowano|`wcscmp`|
|Żaden z symboli nie został zdefiniowany|`strcmp`|

> [!NOTE]
> Symbole _MBCS i _UNICODE wzajemnie się wykluczają.

Mapowania funkcji tekstu ogólnego dla wszystkich procedur obsługi ciągów w czasie wykonywania są omówione w [odwołaniu do biblioteki w czasie wykonywania języka C](../c-runtime-library/c-run-time-library-reference.md). Aby uzyskać listę, zobacz [Internacjonalizacja](../c-runtime-library/internationalization.md).

Podobnie `CString` metody są implementowane przy użyciu mapowania typów danych ogólnych. Aby włączyć zarówno MBCS, jak i Unicode, MFC używa TCHAR `wchar_t*`dla **char** lub `wchar_t`, LPTSTR dla **char** <strong>\*</strong> lub , i LPCTSTR dla **const char** <strong>\*</strong> lub `const wchar_t*`. Zapewniają one poprawne mapowania dla MBCS lub Unicode.

## <a name="see-also"></a>Zobacz też

[Ciągi (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[Manipulowanie ciągami](../c-runtime-library/string-manipulation-crt.md)
