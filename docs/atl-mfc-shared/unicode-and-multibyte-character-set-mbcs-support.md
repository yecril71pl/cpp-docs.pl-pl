---
title: "Unicode i znaków wielobajtowych (MBCS) obsługi zestawu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords:
- MFC [C++], character set support
- MBCS [C++], strings and MFC support
- strings [C++], MBCS support in MFC
- character sets [C++], multibyte
- Unicode [C++], MFC strings
- Unicode [C++], string objects
- strings [C++], Unicode
- strings [C++], character set support
ms.assetid: 44b3193b-c92d-40c5-9fa8-5774da303cce
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 08f15fd57cb1354399e4e85b886141d02cb49daa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="unicode-and-multibyte-character-set-mbcs-support"></a>Unicode i znaków wielobajtowych (MBCS) obsługi zestawu
Niektóre języki, na przykład, japońskim i chiński, są dużych zestawach znaków. Aby zapewnić obsługę programowania dla tych rynkach, Biblioteka Microsoft Foundation Class (MFC) jest włączona na dwa różne podejścia do obsługi dużych zestawów:  
  
-   [Unicode](#_core_mfc_support_for_unicode_strings)  
  
-   [Zestawy znaków wielobajtowych (MBCS)](#_core_mfc_support_for_mbcs_strings)  
  
 Należy użyć Unicode dla wszystkich nowych wdrożeń.  
  
##  <a name="_core_mfc_support_for_unicode_strings"></a>Obsługa MFC dla ciągów Unicode  
 Biblioteka klas całego warunkowo jest włączona dla znaków Unicode i ciągów. W szczególności klasy [cstring —](../atl-mfc-shared/reference/cstringt-class.md) obsługuje standard Unicode.  
  
|||||  
|-|-|-|-|  
|UAFXCW. LIB|UAFXCW. PDB|UAFXCWD. LIB|UAFXCWD. PDB|  
|MFC*xx*U.LIB|MFC*xx*U.PDB|MFC*xx*U.DLL|MFC*xx*UD. LIB|  
|MFC*xx*UD. PDB|MFC*xx*UD. BIBLIOTEKI DLL|MFCS*xx*U.LIB|MFCS*xx*U.PDB|  
|MFCS*xx*UD. LIB|MFCS*xx*UD. PDB|MFCM*xx*U.LIB|MFCM*xx*U.PDB|  
|MFCM*xx*U.DLL|MFCM*xx*UD. LIB|MFCM*xx*UD. PDB|MFCM*xx*UD. BIBLIOTEKI DLL|  
  
 (*xx* reprezentuje numer wersji pliku, np; na przykład "80" oznacza wersji 8.0.)  
  
 `CString`jest oparta na `TCHAR` — typ danych. Jeśli symbolu `_UNICODE` jest zdefiniowany dla kompilacji programu, `TCHAR` jest zdefiniowany jako typ `wchar_t`, typ kodowania znaków 16-bitowych. W przeciwnym razie `TCHAR` jest zdefiniowany jako `char`, kodowanie normalne znaki 8-bitową. W związku z tym w kodowaniu Unicode `CString` składa się z 16-bitowe znaki. Bez Unicode, składa się z znaków typu `char`.  
  
 Do ukończenia programowania Unicode aplikacji, należy również:  
  
-   Użyj `_T` makro warunkowo kodu ciągi literałów jako przenośne na ciąg Unicode.  
  
-   Podczas przekazywania ciągów należy zwrócić uwagę, czy argumenty funkcji wymagające długość w znakach lub długość w bajtach. Różnica jest ważne, jeśli używasz ciągów Unicode.  
  
-   Użyj wersji przenośne funkcje obsługi ciągów środowiska wykonawczego języka C.  
  
-   Użyj następujących typów danych znaków i wskaźniki znaków:  
  
    -   `TCHAR`Gdy używasz `char`.  
  
    -   `LPTSTR`Gdy używasz `char*`.  
  
    -   `LPCTSTR`Gdy używasz `const char*`. `CString`zawiera operator `LPCTSTR` konwersję między `CString` i `LPCTSTR`.  
  
 `CString`udostępnia również obsługujących Unicode konstruktorów operatory przypisania i operatory porównania.  
  
 Powiązane informacje na programowania Unicode, zobacz [tematy Unicode](../mfc/unicode-in-mfc.md). [Odwołanie do biblioteki wykonawczej](../c-runtime-library/c-run-time-library-reference.md) definiuje przenośne wersje wszystkich funkcji obsługi ciągów. Zobacz kategorii [internacjonalizacji](../c-runtime-library/internationalization.md).  
  
##  <a name="_core_mfc_support_for_mbcs_strings"></a>Obsługa MFC dla ciągów MBCS  
  
 Biblioteka klas jest również włączone dla zestawów znaków wielobajtowych, ale tylko w przypadku znaków dwubajtowych ustawia (DBCS).  
  
 W zestawie znaków wielobajtowych znak może być jeden lub dwa bajty szerokości. Dwa bajty szerokości, jego pierwszego bajtu jest specjalnego "bajtu" który jest wybrane z określonego zakresu, w zależności od tego, które kodu strony jest używany. Razem potencjalnych klientów i "końcu bajtów" Określ kodowanie znaków na unikatowy.  
  
 Jeśli symbolu `_MBCS` jest zdefiniowany dla kompilacji programu typu `TCHAR`, na którym `CString` bazuje, mapuje `char`. Pozwala określić, które bajtów jest `CString` są realizacji bajtów, które są dziennik bajtów. Biblioteki wykonawcze języka C udostępnia funkcje ułatwiające to ustalić.  
  
 W obszarze zestawów znaków Dwubajtowych dany ciąg znaków może zawierać znaki jednobajtowe ANSI, wszystkie znaki dwubajtowe lub połączenie tych dwóch. Te możliwości wymagają szczególną w analizowanie ciągów. Dotyczy to również `CString` obiektów.  
  
> [!NOTE]
>  Serializacji ciągu Unicode w MFC mogą odczytywać zarówno Unicode i MBCS ciągi niezależnie od tego, która wersja aplikacji, które są uruchomione. Pliki danych można przenosić między wersjami Unicode i MBCS programu.  
  
 `CString`Funkcje Członkowskie użyć wersji specjalne "zwykłego tekstu" funkcje wykonawcze języka C, które wywołują lub ich funkcje świadomi Unicode. W związku z tym, na przykład jeśli `CString` zwykle spowodowałoby wywołanie funkcji `strcmp`, wywołuje funkcję odpowiedniego zwykłego tekstu `_tcscmp` zamiast tego. W zależności od tego, jak symbole `_MBCS` i `_UNICODE` są zdefiniowane `_tcscmp` mapy w następujący sposób:  
  
|||  
|-|-|  
|`_MBCS`Definicja|`_mbscmp`|  
|`_UNICODE`Definicja|`wcscmp`|  
|Żadna symbol zdefiniowany|`strcmp`|  
  
> [!NOTE]
>  Symbole `_MBCS` i `_UNICODE` wzajemnie się wykluczają.  
  
 Mapowania zwykłego tekstu funkcji dla wszystkich czasu wykonywania procedury obsługi ciągów, omówiono w [odwołanie do biblioteki C Run-Time](../c-runtime-library/c-run-time-library-reference.md). W szczególności, zobacz [internacjonalizacji](../c-runtime-library/internationalization.md).  
  
 Podobnie `CString` metody są implementowane za pomocą mapowanie typu danych "Ogólne". Aby włączyć zarówno MBCS i Unicode, używa MFC `TCHAR` dla `char`, `LPTSTR` dla `char*`, i `LPCTSTR` dla `const char*`. Te zapewnić poprawne mapowania MBCS lub Unicode.  
  
## <a name="see-also"></a>Zobacz też  
 [Ciągi (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)   
 [Manipulowanie ciągami](../c-runtime-library/string-manipulation-crt.md)

