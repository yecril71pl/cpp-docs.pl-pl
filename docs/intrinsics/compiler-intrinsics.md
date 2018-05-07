---
title: Funkcje wewnętrzne kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- intrinsics, compiler
- compiler intrinsics
- cl.exe compiler, performance
- cl.exe compiler, intrinsics
ms.assetid: 48bb9929-7d78-4fd8-a092-ae3c9f971858
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c05a2843e5daff980d1c84d4d3f2185ac361144d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-intrinsics"></a>Funkcje wewnętrzne kompilatora
Większość funkcji są zawarte w bibliotekach, ale niektóre funkcje są wbudowane w (to znaczy wewnętrzna) do kompilatora. Te są określane jako funkcje wewnętrzne lub funkcje wewnętrzne.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli funkcja wewnętrzna, kod dla tej funkcji jest zwykle wstawiony w tekście, umożliwia uniknięcie przeciążenia wywołanie funkcji, dzięki czemu maszyny wysoce efektywne instrukcjami, aby emitować dla tej funkcji. Wewnętrznie jest często szybsze niż w zestawie wbudowanym równoważne, ponieważ Optymalizator ma wbudowane znajomości zachowywać się jak wiele funkcje wewnętrzne, więc niektóre funkcje optymalizacji mogą być dostępne który są niedostępne, gdy jest używany zestaw wbudowany. Ponadto Optymalizator można rozwinąć wewnętrzne inaczej, inaczej Dopasuj buforów lub dostosować inne w zależności od kontekstu i argumenty wywołania.  
  
 Użycie funkcji wewnętrznych ma wpływ na przenośność kodu, ponieważ funkcje wewnętrzne, które są dostępne w programie Visual C++ mogą nie być dostępne niektóre funkcje wewnętrzne, które mogą być dostępne dla niektórych architektury docelowej nie są dostępne, jeśli kod jest skompilowana przy użyciu inne kompilatory dla wszystkich architektur. Jednak funkcje wewnętrzne są zazwyczaj przenośną niż wbudowany zestaw. Funkcje wewnętrzne są wymagane w 64-bitowych architektury, których wbudowany zestaw nie jest obsługiwana.  
  
 Niektóre funkcje wewnętrzne, takie jak `__assume` i `__ReadWriteBarrier`, zawierają informacje, które kompilator, który ma wpływ na zachowanie optymalizatora.  
  
 Niektóre funkcje wewnętrzne są dostępne tylko jako funkcje wewnętrzne, a niektóre są dostępne zarówno w wewnętrznej implementacji i funkcji. Możesz wydać kompilator, aby użyć wewnętrznej implementacji w jeden z dwóch sposobów, w zależności od tego, czy chcesz włączyć tylko określonych funkcji lub chcesz włączyć wszystkie funkcje wewnętrzne. Pierwszym sposobem jest użycie `#pragma intrinsic(` *wewnętrzne — funkcja-— lista nazw*`)`. Pragma może służyć do określenia wewnętrzne jedną lub wiele funkcji wewnętrznych rozdzielonych przecinkami. Druga to użycie [/Oi (Generuj funkcje wewnętrzne)](../build/reference/oi-generate-intrinsic-functions.md) opcję kompilatora, która udostępnia wszystkie funkcje wewnętrzne na danej platformie. W obszarze **/Oi**, użyj `#pragma function(` *wewnętrzne — funkcja-— lista nazw* `)` wymusić wywołanie funkcji do użycia zamiast wewnętrznie. Jeśli w dokumentacji konkretnego — wewnętrzne zauważyła, że procedura jest dostępna jako funkcja wewnętrzna tylko, a następnie wewnętrznej implementacji jest używany niezależnie od tego, czy **/Oi** lub `#pragma intrinsic` jest określona. We wszystkich przypadkach **/Oi** lub `#pragma intrinsic` umożliwia, ale nie wymusza Optymalizator do używania wewnętrznej. Optymalizator nadal można wywołać funkcji.  
  
 Niektóre standardowe funkcje biblioteki C/C++ są dostępne w wewnętrznych we wdrożeniach w systemie niektórych architektury. Podczas wywoływania funkcji CRT, wewnętrznej implementacji jest używana, gdy **/Oi** jest określona w wierszu polecenia.  
  
 Plik nagłówka \<intrin.h >, jest dostępna, która deklaruje prototypy dla typowych funkcji wewnętrznej. Funkcje wewnętrzne specyficzne dla producenta są dostępne w \<immintrin.h > i \<ammintrin.h > Pliki nagłówków. Ponadto niektóre nagłówków systemu Windows zadeklarować funkcji, które mapują na wewnętrznych kompilatora.  
  
 W poniższych sekcjach wymieniono wszystkie funkcje wewnętrzne, które są dostępne w różnych architektur. Więcej informacji na temat działania funkcje wewnętrzne na procesor określonego elementu docelowego można znaleźć w dokumentacji producenta.  
  
-   [Funkcje wewnętrzne ARM](../intrinsics/arm-intrinsics.md)  
  
-   [Lista funkcji wewnętrznych x86](../intrinsics/x86-intrinsics-list.md)  
  
-   [Lista funkcji wewnętrznych x64 (amd64)](../intrinsics/x64-amd64-intrinsics-list.md)  
  
-   [Funkcje wewnętrzne dostępne we wszystkich architekturach](../intrinsics/intrinsics-available-on-all-architectures.md)  
  
-   [Alfabetyczna lista funkcji wewnętrznych](../intrinsics/alphabetical-listing-of-intrinsic-functions.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do asemblera ARM](../assembler/arm/arm-assembler-reference.md)   
 [Microsoft Macro Assembler — odwołanie](../assembler/masm/microsoft-macro-assembler-reference.md)   
 [Keywords](../cpp/keywords-cpp.md)   
 [Dokumentacja biblioteki środowiska uruchomieniowego języka C](../c-runtime-library/c-run-time-library-reference.md)