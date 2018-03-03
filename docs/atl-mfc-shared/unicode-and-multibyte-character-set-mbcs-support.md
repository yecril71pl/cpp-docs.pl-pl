---
title: "Unicode i znaków wielobajtowych (MBCS) obsługi zestawu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 1/09/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: adbe6ca25afd31c0aba853fde8b503dc333f63f4
ms.sourcegitcommit: 56f6fce7d80e4f61d45752f4c8512e4ef0453e58
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2018
---
# <a name="unicode-and-multibyte-character-set-mbcs-support"></a>Unicode i znaków wielobajtowych (MBCS) obsługi zestawu

Niektóre języki, na przykład, japońskim i chiński, są dużych zestawach znaków. Aby zapewnić obsługę programowania dla tych rynkach, Biblioteka Microsoft Foundation Class (MFC) umożliwia dwa różne podejścia do obsługi dużych zestawów:

- [Unicode](#mfc-support-for-unicode-strings), `wchar_t` na podstawie całej znaków i ciągi zakodowane jako UTF-16.

- [Zestawy znaków wielobajtowych (MBCS)](#mfc-support-for-mbcs-strings), `char` na podstawie pojedynczego lub dwubajtowych znaków i ciągi zakodowane w zestawie znaków specyficzne dla ustawień regionalnych.

Microsoft zaleciła biblioteki MFC Unicode dla wszystkich nowych wdrożeniach i bibliotek MBCS były przestarzałe w programie Visual Studio 2013 i Visual Studio 2015. Obecnie taka ewentualność nie zachodzi. Ostrzeżenia dotyczące zaniechania MBCS zostały usunięte z programu Visual Studio 2017 r.

## <a name="mfc-support-for-unicode-strings"></a>Obsługa MFC dla ciągów Unicode

Cała biblioteka klas MFC warunkowo jest włączony dla znaków Unicode i ciągi w znaki dwubajtowe przechowywane jako UTF-16. W szczególności klasy [cstring —](../atl-mfc-shared/reference/cstringt-class.md) obsługuje standard Unicode.

Te biblioteki debugera i pliki DLL są używane do obsługi standardu Unicode w MFC:

|||||
|-|-|-|-|
|UAFXCW. LIB|UAFXCW. PDB|UAFXCWD. LIB|UAFXCWD. PDB|
|MFC*wersji*U.LIB|MFC*wersji*U.PDB|MFC*wersji*U.DLL|MFC*wersji*UD. LIB|
|MFC*wersji*UD. PDB|MFC*wersji*UD. BIBLIOTEKI DLL|MFCS*wersji*U.LIB|MFCS*wersji*U.PDB|
|MFCS*wersji*UD. LIB|MFCS*wersji*UD. PDB|MFCM*wersji*U.LIB|MFCM*wersji*U.PDB|
|MFCM*wersji*U.DLL|MFCM*wersji*UD. LIB|MFCM*wersji*UD. PDB|MFCM*wersji*UD. BIBLIOTEKI DLL|

(*wersji* reprezentuje numer wersji pliku, np; na przykład "140" oznacza wersji 14.0.)

`CString`jest oparta na `TCHAR` — typ danych. Jeśli symbolu `_UNICODE` jest zdefiniowany dla kompilacji programu, `TCHAR` jest zdefiniowany jako typ `wchar_t`, typ kodowania znaków 16-bitowych. W przeciwnym razie `TCHAR` jest zdefiniowany jako `char`, kodowanie normalne znaki 8-bitową. W związku z tym w kodowaniu Unicode `CString` składa się z 16-bitowe znaki. Bez Unicode, składa się z znaków typu `char`.

Do ukończenia programowania Unicode aplikacji, należy również:

- Użyj `_T` makro warunkowo kodu ciągi literałów jako przenośne na ciąg Unicode.

- Podczas przekazywania ciągów należy zwrócić uwagę, czy argumenty funkcji wymagające długość w znakach lub długość w bajtach. Różnica jest ważne, jeśli używasz ciągów Unicode.

- Użyj wersji przenośne funkcje obsługi ciągów środowiska wykonawczego języka C.

- Użyj następujących typów danych znaków i wskaźniki znaków:

   - Użyj `TCHAR` użycia `char`.

   - Użyj `LPTSTR` użycia `char*`.

   - Użyj `LPCTSTR` użycia `const char*`. `CString`zawiera operator `LPCTSTR` konwersję między `CString` i `LPCTSTR`.

`CString`udostępnia również obsługujących Unicode konstruktorów operatory przypisania i operatory porównania.

[Odwołanie do biblioteki wykonawczej](../c-runtime-library/c-run-time-library-reference.md) definiuje przenośne wersje wszystkich funkcji obsługi ciągów. Aby uzyskać więcej informacji, zobacz kategorii [internacjonalizacji](../c-runtime-library/internationalization.md).

## <a name="mfc-support-for-mbcs-strings"></a>Obsługa MFC dla ciągów MBCS

Biblioteka klas jest również włączone dla zestawów znaków wielobajtowych, ale tylko w przypadku znaków dwubajtowych ustawia (DBCS).

W zestawie znaków wielobajtowych znak może być jeden lub dwa bajty szerokości. Dwa bajty szerokości, jego pierwszego bajtu jest specjalnego "bajtu" który jest wybrane z określonego zakresu, w zależności od tego, które kodu strony jest używany. Razem potencjalnych klientów i "końcu bajtów" Określ kodowanie znaków na unikatowy.

Jeśli symbolu `_MBCS` jest zdefiniowany dla kompilacji programu typu `TCHAR`, na którym `CString` bazuje, mapuje `char`. Pozwala określić, które bajtów jest `CString` są realizacji bajtów, które są dziennik bajtów. Biblioteki wykonawcze języka C udostępnia funkcje ułatwiające to ustalić.

W obszarze zestawów znaków Dwubajtowych dany ciąg znaków może zawierać znaki jednobajtowe ANSI, wszystkie znaki dwubajtowe lub połączenie tych dwóch. Te możliwości wymagają szczególną w analizowanie ciągów. Dotyczy to również `CString` obiektów.

> [!NOTE]
> Serializacji ciągu Unicode w MFC mogą odczytywać zarówno Unicode i MBCS ciągi niezależnie od tego, która wersja aplikacji, które są uruchomione. Pliki danych można przenosić między wersjami Unicode i MBCS programu.

`CString`Funkcje Członkowskie użyć wersji specjalne "zwykłego tekstu" funkcje wykonawcze języka C, które wywołują lub ich funkcje świadomi Unicode. W związku z tym, na przykład jeśli `CString` zwykle spowodowałoby wywołanie funkcji `strcmp`, wywołuje funkcję odpowiedniego zwykłego tekstu `_tcscmp` zamiast tego. W zależności od tego, jak symbole `_MBCS` i `_UNICODE` są zdefiniowane `_tcscmp` mapy w następujący sposób:

|||
|-|-|
|`_MBCS`Definicja|`_mbscmp`|
|`_UNICODE`Definicja|`wcscmp`|
|Żadna symbol zdefiniowany|`strcmp`|

> [!NOTE]
> Symbole `_MBCS` i `_UNICODE` wzajemnie się wykluczają.

Mapowania zwykłego tekstu funkcji dla wszystkich czasu wykonywania procedury obsługi ciągów, omówiono w [odwołanie do biblioteki C Run-Time](../c-runtime-library/c-run-time-library-reference.md). Aby uzyskać listę, zobacz [internacjonalizacji](../c-runtime-library/internationalization.md).

Podobnie `CString` metody są implementowane za pomocą mapowania typów danych typu ogólnego. Aby włączyć zarówno MBCS i Unicode, używa MFC `TCHAR` dla `char` lub `wchar_t`, `LPTSTR` dla `char*` lub `wchar_t*`, i `LPCTSTR` dla `const char*` lub `const wchar_t*`. Te zapewnić poprawne mapowania MBCS lub Unicode.

## <a name="see-also"></a>Zobacz też

[Ciągi (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)  
[Manipulowanie ciągami](../c-runtime-library/string-manipulation-crt.md)  
