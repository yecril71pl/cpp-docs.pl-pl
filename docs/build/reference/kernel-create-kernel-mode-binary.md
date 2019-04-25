---
title: /kernel (Utwórz plik binarny trybu jądra)
ms.date: 11/04/2016
f1_keywords:
- /kernel
- /kernel-
ms.assetid: 6d7fdff0-c3d1-4b78-9367-4da588ce8b05
ms.openlocfilehash: d065364cf6d3ae824098634c070f3651324aa52a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291343"
---
# <a name="kernel-create-kernel-mode-binary"></a>/kernel (Utwórz plik binarny trybu jądra)

Tworzy plik binarny, który może zostać wykonany w jądrze Windows.

## <a name="syntax"></a>Składnia

```
/kernel[-]
```

## <a name="arguments"></a>Argumenty

**/kernel**<br/>
Kod w bieżącym projekcie są kompilowane i połączone za pomocą zestawu reguł języka C++, które są specyficzne dla kodu, który będzie uruchamiany w trybie jądra.

**/Kernel-**<br/>
Kod w bieżącym projekcie są kompilowane i połączone bez korzystania z reguł języka C++, które są specyficzne dla kodu, który będzie uruchamiany w trybie jądra.

## <a name="remarks"></a>Uwagi

Istnieje nie `#pragma` równoważne do kontrolowania tej opcji.

Określanie **/Kernel** opcja informuje kompilator i konsolidator przeprowadzić rozstrzygnięcia, które funkcje języka są dozwolone w trybie jądra i upewnij się, że masz wystarczające siłą, aby zapobiec niestabilności środowiska uruchomieniowego, który jest unikatowy dla Tryb jądra C++. Jest to realizowane w wyniku zabronienia korzystanie z funkcji języka C++, które są one w trybie jądra i udostępnienie ostrzeżenia dla funkcji języka C++, które są potencjalnie szkodliwe, ale nie może być wyłączony.

**/Kernel** opcja ma zastosowanie do kompilatora i konsolidatora fazy kompilacji i jest ustawiona na poziomie projektu. Przekaż **/Kernel** przełącznika, aby poinformować kompilator, że wynikowego pliku binarnego, po połączeniu, powinny być załadowane do jądra Windows. Kompilator będzie zawęzić szerokim zakresie funkcji języka C++ do podzbioru, który jest zgodny z jądra.

W poniższej tabeli wymieniono zmiany w zachowaniu kompilatora podczas **/Kernel** jest określony.

|Typ zachowania|**/ Kernel** zachowanie|
|-------------------|---------------------------|
|Obsługa wyjątków języka C++|Wyłączone. Wszystkie wystąpienia elementu `throw` i `try` słowa kluczowe emitować błąd kompilatora (z wyjątkiem Specyfikacja wyjątku `throw()`). Nie **/EH** opcji są zgodne z **/Kernel**, z wyjątkiem **/EH-**.|
|RTTI|Wyłączone. Wszystkie wystąpienia elementu `dynamic_cast` i `typeid` słowa kluczowe emitować błąd kompilatora, chyba że `dynamic_cast` służy statycznie.|
|`new` i `delete`|Musisz jawnie zdefiniować `new()` lub `delete()` operator; kompilator ani środowisko uruchomieniowe będzie dostarczać definicję domyślną.|

Konwencje wywoływania, niestandardowe [/GS](gs-buffer-security-check.md) opcji kompilacji, a wszystkie optymalizacje są dozwolone, gdy używasz **/Kernel** opcji. Wbudowanie stopniu nie dotyczy **/Kernel**, z tą samą semantyką uznawane przez kompilator. Jeśli chcesz upewnić się, że `__forceinline` wbudowanie kwalifikator jest honorowane, musisz upewnić się, że ostrzeżenie [C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md) jest włączone, dzięki czemu będzie wiadomo, gdy konkretny `__forceinline` funkcja nie jest śródwierszowa.

Gdy kompilator jest przekazywany **/Kernel** przełącznika go powoduje wstępne definiowanie makro preprocesora, który nosi nazwę `_KERNEL_MODE` i ma wartość **1**. Możesz użyć tego, aby warunkowo skompilować kod w oparciu o tego, czy środowisko wykonawcze w trybie użytkownika lub w trybie jądra. Na przykład poniższy kod określa, że klasa mają zostać w segmencie pamięci niestronicowanej, gdy jest ona kompilowana do wykonywania w trybie jądra.

```cpp
#ifdef _KERNEL_MODE
#define NONPAGESECTION __declspec(code_seg("$kerneltext$"))
#else
#define NONPAGESECTION
#endif

class NONPAGESECTION MyNonPagedClass
{
   // ...
};
```

Niektóre następujących kombinacji Architektura docelowa i **/arch** opcji powodować błąd, gdy są one używane z **/Kernel**:

- **/ arch: {SSE&#124;SSE2&#124;AVX}** nie są obsługiwane w x86. Tylko **/arch:IA32** jest obsługiwane w przypadku **/Kernel** na x86.

- **/ arch:** nie jest obsługiwany przez **/Kernel** na x64.

Kompilowanie z użyciem **/Kernel** przekazuje także **/Kernel** do konsolidatora. Jest jej, jak ma to wpływ na zachowanie konsolidatora:

- Łączenie przyrostowe jest wyłączone. Jeśli dodasz **/ incremental** do wiersza polecenia konsolidatora emituje to błąd krytyczny:

   **LINK: błąd krytyczny LNK1295: "/ INCREMENTAL" nie jest zgodna z "/ jądra" Specyfikacja; Link bez "/ INCREMENTAL"**

- Konsolidator sprawdza każdy plik obiektu (lub dowolny członek archiwum uwzględnione w bibliotekach statycznych), aby zobaczyć, czy może on został skompilowany przy użyciu **/Kernel** opcji, jednak podano wartość nie. Jeśli wszystkie wystąpienia spełniać te kryteria, konsolidator nadal pomyślnie łączy, ale może być ostrzeżenie, jak pokazano w poniższej tabeli.

   ||**/ Kernel** obj|**/Kernel-** obj, MASM obj lub cvtresed|Mieszanie z **/Kernel** i **/kernel-** objs|
   |-|----------------------|-----------------------------------------------|-------------------------------------------------|
   |**/ Kernel łącza**|Yes|Yes|Tak, z ostrzeżeniem LNK4257|
   |**link**|Tak|Yes|Tak|

   **LNK4257 obiektu nie został skompilowany z/Kernel; Obraz może nie działać.**

**/Kernel** opcji i **Driver/Driver** opcji działają niezależnie i nie wpływa na drugi.

### <a name="to-set-the-kernel-compiler-option-in-visual-studio"></a>Aby ustawić opcję kompilatora/Kernel w programie Visual Studio

1. Otwórz **stron właściwości** okno dialogowe dla projektu. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **C/C++** folderu.

1. Wybierz **wiersza polecenia** stronę właściwości.

1. W **dodatkowe opcje** Dodaj `/kernel` lub `/kernel-`.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
