---
title: /kernel (Utwórz plik binarny trybu jądra)
ms.date: 11/04/2016
f1_keywords:
- /kernel
- /kernel-
ms.assetid: 6d7fdff0-c3d1-4b78-9367-4da588ce8b05
ms.openlocfilehash: bcef52144e4da932e9e1b6acbcd5f2170c4c7f86
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211947"
---
# <a name="kernel-create-kernel-mode-binary"></a>/kernel (Utwórz plik binarny trybu jądra)

Tworzy plik binarny, który może być wykonywany w jądrze systemu Windows.

## <a name="syntax"></a>Składnia

```
/kernel[-]
```

## <a name="arguments"></a>Argumenty

**/Kernel**<br/>
Kod w bieżącym projekcie jest kompilowany i połączony przy użyciu zestawu reguł języka C++, które są specyficzne dla kodu, który będzie uruchamiany w trybie jądra.

**/Kernel**<br/>
Kod w bieżącym projekcie jest kompilowany i łączony bez używania reguł języka C++, które są specyficzne dla kodu, który będzie uruchamiany w trybie jądra.

## <a name="remarks"></a>Uwagi

Nie ma żadnego `#pragma` równoważnej kontroli tej opcji.

Określenie opcji **/kernel** instruuje kompilator i konsolidator, aby rozstrzygnąć, które funkcje języka są dozwolone w trybie jądra, i upewnić się, że posiadasz wystarczającą moc umożliwiającą uniknięcie niestabilności środowiska uruchomieniowego, która jest unikatowa dla trybu jądra C++. Jest to realizowane przez zabronienie używania funkcji języka C++, które są zakłócone w trybie jądra, oraz zapewnianie ostrzeżeń dotyczących funkcji języka C++, które są potencjalnie zakłócające, ale nie można ich wyłączyć.

Opcja **/kernel** dotyczy faz kompilatora i konsolidatora kompilacji i jest ustawiana na poziomie projektu. Przekaż przełącznik **/kernel** , aby wskazać kompilatorowi, że dane binarne, po konsolidacji, powinny być załadowane do jądra systemu Windows. Kompilator zawęża zakres funkcji języka C++ do podzestawu, który jest zgodny z jądrem.

W poniższej tabeli przedstawiono zmiany zachowania kompilatora, gdy **/kernel** jest określony.

|Typ zachowania|**/kernel** Domyślnie|
|-------------------|---------------------------|
|Obsługa wyjątków języka C++|Wyłączona. Wszystkie wystąpienia **`throw`** **`try`** słowa kluczowego and emitują błąd kompilatora (z wyjątkiem specyfikacji wyjątku `throw()` ). Opcje **/EH** są zgodne z **/kernel**, z wyjątkiem **/EH-**.|
|RTTI|Wyłączona. Wszystkie wystąpienia **`dynamic_cast`** **`typeid`** słowa kluczowego and emitują błąd kompilatora, chyba że **`dynamic_cast`** jest używany statycznie.|
|`new` i `delete`|Należy jawnie zdefiniować `new()` `delete()` operator or; ani kompilator ani środowisko uruchomieniowe nie będą podawać definicji domyślnej.|

Niestandardowe Konwencje wywoływania, opcja kompilacja [/GS](gs-buffer-security-check.md) i wszystkie optymalizacje są dozwolone w przypadku korzystania z opcji **/kernel** . **/Kernel**z tą samą semantyką, która jest w dużym stopniu niezależna od kompilatora. Jeśli chcesz upewnić się **`__forceinline`** , że kwalifikator jest uznawany za niepodkreślanie, musisz upewnić się, że [C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md) ostrzegawczy jest włączony, aby wiedzieć, gdy określona **`__forceinline`** Funkcja nie jest wbudowana.

Gdy kompilator przeszedł przełącznik **/kernel** , wstępnie definiuje makro preprocesora o nazwie `_KERNEL_MODE` i ma wartość **1**. Można go użyć do warunkowego kompilowania kodu w zależności od tego, czy środowisko wykonawcze działa w trybie użytkownika, czy na jądrze. Na przykład poniższy kod określa, że klasa powinna znajdować się w segmencie pamięci bez stronicowania, gdy jest kompilowany do wykonywania w trybie jądra.

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

Niektóre z następujących kombinacji architektury docelowej i opcji **/Arch** generują błąd, gdy są używane z **/kernel**:

- **/arch: {SSE&#124;SSE2&#124;AVX}** nie są obsługiwane w architekturze x86. Tylko **/arch: ia32** jest obsługiwany przez **/kernel** na x86.

- **/arch: AVX** nie jest obsługiwana w przypadku **/kernel** na platformie x64.

Kompilowanie za pomocą **/kernel** powoduje również przekazanie **/kernel** do konsolidatora. Ma to wpływ na zachowanie konsolidatora:

- Łączenie przyrostowe jest wyłączone. Jeśli dodasz **/Incremental** do wiersza polecenia, konsolidator emituje ten błąd krytyczny:

   **LINK: błąd krytyczny LNK1295: "/INCREMENTAL" jest niezgodny ze specyfikacją "/KERNEL"; link bez "/INCREMENTAL"**

- Konsolidator sprawdza każdy plik obiektu (lub dowolny składowa archiwalny z bibliotek statycznych), aby sprawdzić, czy mógł zostać skompilowany przy użyciu opcji **/kernel** , ale nie jest. Jeśli jakieś wystąpienia spełnią to kryterium, konsolidator nadal pomyślnie łączy się, ale może wydać ostrzeżenie, jak pokazano w poniższej tabeli.

   ||**/kernel** obj|**/kernel-** obj, MASM obj lub cvtresed|Mieszanie **/kernel** i **/kernel-** przywołujące obj zawierały|
   |-|----------------------|-----------------------------------------------|-------------------------------------------------|
   |**/Kernel linku**|Tak|Tak|Tak z ostrzeżeniem LNK4257|
   |**powiązań**|Tak|Tak|Tak|

   **LNK4257 łączenie obiektu nie jest kompilowane z/KERNEL; nie można uruchomić obrazu**

Opcja **/kernel** **i polecenie/** /i/+ nie działają niezależnie i nie mają wpływu na pozostałe.

### <a name="to-set-the-kernel-compiler-option-in-visual-studio"></a>Aby ustawić opcję kompilatora/kernel w programie Visual Studio

1. Otwórz okno dialogowe **strony właściwości** dla projektu. Aby uzyskać więcej informacji, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz folder **C/C++** .

1. Wybierz stronę właściwości **wiersza polecenia** .

1. W polu **dodatkowe opcje** Dodaj `/kernel` lub `/kernel-` .

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
