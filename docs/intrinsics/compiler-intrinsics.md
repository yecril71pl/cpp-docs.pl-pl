---
title: Funkcje wewnętrzne kompilatora
ms.date: 11/04/2016
helpviewer_keywords:
- intrinsics, compiler
- compiler intrinsics
- cl.exe compiler, performance
- cl.exe compiler, intrinsics
ms.assetid: 48bb9929-7d78-4fd8-a092-ae3c9f971858
ms.openlocfilehash: 9a014e870d731d7e7d443c3bfefd66884aa50d5d
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59029281"
---
# <a name="compiler-intrinsics"></a>Funkcje wewnętrzne kompilatora

Większość funkcji jest zawartych w bibliotekach, ale niektóre funkcje są wbudowane (to znaczy, wewnętrzne) do kompilatora. Te są nazywane funkcjami wewnętrznymi.

## <a name="remarks"></a>Uwagi

Jeśli funkcja jest wewnętrzna, kod dla tej funkcji jest zwykle wbudowany, unikając obciążenie związane z wywołaniem funkcji, dzięki czemu wysoko wydajnych instrukcji maszynowych dla tej funkcji. Wewnętrzna jest często szybsza niż zestawu równoważnych inline ponieważ Optymalizator ma wbudowaną wiedzę o zachowują się jak wiele obiektów wewnętrznych, więc niektóre optymalizację mogą być dostępne, są niedostępne, gdy jest używany wbudowany zestaw. Ponadto Optymalizator może się inaczej wewnętrznie rozwinąć, wyrównać bufory w inny sposób lub zmienić inne ustawienia w zależności od kontekstu i argumentu wywołania.

Użycie wewnętrznych elementów ma wpływ na Przenoszalność kodu, ponieważ funkcje wewnętrzne, które są dostępne w programie Visual C++ mogą nie być dostępne Jeżeli kod jest kompilowany za pomocą innych kompilatorów i niektóre funkcje wewnętrzne, które mogą być dostępne dla docelowych architektur nie są dostępne dla wszystkich architektur. Jednakże funkcje wewnętrzne są zwykle bardziej przenośne niż wbudowane zestawy. Funkcje wewnętrzne są wymagane w 64-bitowych architekturach, gdzie wbudowany zestaw nie jest obsługiwany.

Niektóre funkcje wewnętrzne, takie jak `__assume` i `__ReadWriteBarrier`, podaj informacje potrzebne do kompilatora, który ma wpływ na zachowanie optymalizatora.

Niektóre funkcje wewnętrzne są dostępne tylko jako funkcje wewnętrzne, a niektóre są dostępne zarówno w funkcji i wewnętrzne implementacje. Można poinstruować kompilator, aby użył wewnętrznych implementacji na jeden z dwóch sposobów, w zależności od tego, czy chcesz włączyć tylko konkretne funkcje, lub jeśli chcesz włączyć wszystkie wewnętrzne. Pierwszym sposobem jest użycie `#pragma intrinsic(` *wewnętrzne funkcja nazwa list*`)`. Pragmy może służyć do określenia pojedynczego wewnętrznego lub wielu wewnętrznych elementów oddzielonych przecinkami. Druga służy wykorzystaniu [/Oi (Generuj funkcje wewnętrzne)](../build/reference/oi-generate-intrinsic-functions.md) opcji kompilatora, która udostępnia wszystkie elementy wewnętrzne na danej platformie. W obszarze **/Oi**, użyj `#pragma function(` *wewnętrzne funkcja nazwa list* `)` Aby wymusić wywołanie funkcji ma być używana zamiast wewnętrzna. Jeśli w dokumentacji poszczególnych funkcji wewnętrznych jest napisane, że procedura jest dostępna jako funkcja wewnętrzna tylko, a następnie wdrożenie wewnętrzne zostanie użyte niezależnie od tego, czy **/Oi** lub `#pragma intrinsic` jest określony. We wszystkich przypadkach **/Oi** lub `#pragma intrinsic` pozwala, ale nie wymusza wewnętrznego użycia przez optymalizator. Optymalizacja może wciąż wywołać funkcję.

Niektóre standardowe funkcje biblioteki C/C++ są dostępne w wewnętrznych implementacjach na niektórych architekturach. Podczas wywoływania funkcji CRT, niejawna implementacja jest użyta, jeśli **/Oi** jest określona w wierszu polecenia.

Plik nagłówka \<intrin.h >, jest dostępna, która deklaruje prototypy typowe funkcje wewnętrzne. Funkcje specyficzne dla producenta wewnętrzne są dostępne w \<immintrin.h > i \<ammintrin.h > pliki nagłówkowe. Dodatkowo niektóre nagłówki Windows deklarują funkcje, które mapują na wewnętrzne kompilatora.

W poniższych sekcjach wymieniono wszystkie funkcje wewnętrzne, które są dostępne w różnych architekturach. Aby uzyskać więcej informacji na temat sposobu działania funkcji wewnętrznych na Twoim procesorze zapoznaj się z dokumentacją producenta.

- [Funkcje wewnętrzne ARM](../intrinsics/arm-intrinsics.md)

- [Lista funkcji wewnętrznych x86](../intrinsics/x86-intrinsics-list.md)

- [Lista funkcji wewnętrznych x64 (amd64)](../intrinsics/x64-amd64-intrinsics-list.md)

- [Funkcje wewnętrzne dostępne we wszystkich architekturach](../intrinsics/intrinsics-available-on-all-architectures.md)

- [Alfabetyczna lista funkcji wewnętrznych](../intrinsics/alphabetical-listing-of-intrinsic-functions.md)

## <a name="see-also"></a>Zobacz także

[Dokumentacja asemblera ARM](../assembler/arm/arm-assembler-reference.md)<br/>
[Microsoft Macro Assembler — dokumentacja](../assembler/masm/microsoft-macro-assembler-reference.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[Dokumentacja biblioteki środowiska uruchomieniowego języka C](../c-runtime-library/c-run-time-library-reference.md)