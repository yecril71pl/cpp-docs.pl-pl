---
title: Funkcje wewnętrzne kompilatora
ms.date: 09/02/2019
helpviewer_keywords:
- intrinsics, compiler
- compiler intrinsics
- cl.exe compiler, performance
- cl.exe compiler, intrinsics
ms.assetid: 48bb9929-7d78-4fd8-a092-ae3c9f971858
ms.openlocfilehash: 6f41b56995e1a5a7d7f4267cb1def5370f953d5c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171674"
---
# <a name="compiler-intrinsics"></a>Funkcje wewnętrzne kompilatora

Większość funkcji znajduje się w bibliotekach, ale niektóre funkcje są wbudowane (czyli wewnętrznie) do kompilatora. Są one określane jako funkcje wewnętrzne lub wewnętrzne.

## <a name="remarks"></a>Uwagi

Jeśli funkcja jest wewnętrzną, kod dla tej funkcji jest zwykle wstawiany wewnętrznie, unikając obciążenia wywołania funkcji i umożliwiającego emitowanie wysoko wydajnych instrukcji maszynowych dla tej funkcji. Wewnętrzny jest często szybszy niż odpowiednik wbudowanego zestawu, ponieważ Optymalizator ma wbudowaną wiedzę o liczbie zastosowanych elementów wewnętrznych, dlatego niektóre optymalizacje mogą być dostępne, które nie są dostępne, gdy używany jest zestaw wbudowany. Ponadto Optymalizator może zwiększyć wewnętrzną zmianę, wyrównać bufory inaczej lub wprowadzić inne korekty w zależności od kontekstu i argumentów wywołania.

Użycie funkcji wewnętrznych ma wpływ na przenośność kodu, ponieważ wewnętrzne, które są dostępne w wizualizacji C++ , mogą nie być dostępne, jeśli kod jest kompilowany z innymi kompilatorami, a niektóre funkcje wewnętrzne, które mogą być dostępne dla niektórych architektur docelowych, nie są dostępne dla wszystkich architektur. Jednak funkcje wewnętrzne są zwykle bardziej przenośne niż zestaw wbudowany. Elementy wewnętrzne są wymagane na 64-bitowych architekturach, w których Wbudowany zestaw nie jest obsługiwany.

Niektóre funkcje wewnętrzne, takie jak `__assume` i `__ReadWriteBarrier`, zawierają informacje dla kompilatora, które mają wpływ na zachowanie optymalizatora.

Niektóre funkcje wewnętrzne są dostępne tylko jako elementy wewnętrzne, a niektóre z nich są dostępne zarówno w funkcjach, jak i wewnętrznie. Możesz nakazać kompilatorowi użycie wewnętrznej implementacji na jeden z dwóch sposobów, w zależności od tego, czy chcesz włączyć tylko określone funkcje, czy chcesz włączyć wszystkie elementy wewnętrzne. Pierwszy sposób to użycie`)``#pragma intrinsic(`*wewnętrznego-Name-list* . Dyrektywy pragma można użyć do określenia jednego wewnętrznego lub wielu elementów wewnętrznych rozdzielonych przecinkami. Drugim jest użycie opcji kompilatora [/Oi (Generuj funkcje wewnętrzne)](../build/reference/oi-generate-intrinsic-functions.md) , która sprawia, że wszystkie elementy wewnętrzne na danej platformie są dostępne. Aby wymusić użycie wywołania funkcji zamiast wewnętrznego, w obszarze **/Oi**należy `#pragma function(`użyć`)` z *listy nazw wewnętrznych funkcji* . Jeśli Dokumentacja dla określonych wewnętrznych informacji jest dostępna tylko jako wewnętrzna, to implementacja wewnętrzna jest używana bez względu na to, czy określono **/Oi** lub `#pragma intrinsic`. We wszystkich przypadkach **/Oi** lub `#pragma intrinsic` zezwala, ale nie wymusza użycia wewnętrznego przez optymalizator. Optymalizator nadal może wywołać funkcję.

Niektóre standardowe funkcje językaC++ C/library są dostępne w implementacjach wewnętrznych w niektórych architekturach. Podczas wywoływania funkcji CRT, implementacja wewnętrzna jest używana, jeśli **/Oi** jest określony w wierszu polecenia.

Jest dostępny plik nagłówka \<intrin. h >, który deklaruje prototypy dla wspólnych funkcji wewnętrznych. Elementy wewnętrzne specyficzne dla producenta są dostępne w \<immintrin. h > i \<ammintrin. h > plików nagłówkowych. Ponadto niektóre nagłówki systemu Windows deklarują funkcje, które są mapowane na wewnętrzne kompilator.

W poniższych sekcjach wymieniono wszystkie funkcje wewnętrzne, które są dostępne w różnych architekturach. Aby uzyskać więcej informacji na temat sposobu działania elementów roboczych na określonym procesorze docelowym, zapoznaj się z dokumentacją producenta.

- [Funkcje wewnętrzne ARM](../intrinsics/arm-intrinsics.md)

- [ARM64 wewnętrzne](../intrinsics/arm64-intrinsics.md)

- [Lista funkcji wewnętrznych x86](../intrinsics/x86-intrinsics-list.md)

- [Lista funkcji wewnętrznych x64 (amd64)](../intrinsics/x64-amd64-intrinsics-list.md)

- [Elementy wewnętrzne dostępne we wszystkich architekturach](../intrinsics/intrinsics-available-on-all-architectures.md)

- [Alfabetyczna lista funkcji wewnętrznych](../intrinsics/alphabetical-listing-of-intrinsic-functions.md)

## <a name="see-also"></a>Zobacz też

[Dokumentacja asemblera ARM](../assembler/arm/arm-assembler-reference.md)<br/>
[Dokumentacja asemblera programu Microsoft Macro](../assembler/masm/microsoft-macro-assembler-reference.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[Dokumentacja biblioteki wykonawczej języka C](../c-runtime-library/c-run-time-library-reference.md)
