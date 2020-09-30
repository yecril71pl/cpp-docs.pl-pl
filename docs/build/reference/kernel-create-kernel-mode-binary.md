---
title: /kernel (Utwórz plik binarny trybu jądra)
description: Opcja/kernel kompilatora Microsoft C/C++ kompiluje i łączy projekty dla wykonywania w trybie jądra.
ms.date: 09/28/2020
f1_keywords:
- /kernel
- /kernel-
ms.assetid: 6d7fdff0-c3d1-4b78-9367-4da588ce8b05
ms.openlocfilehash: 8a8c02a6f102a52afbc52c154ce215ede3f38f74
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509356"
---
# <a name="kernel-create-kernel-mode-binary"></a>/kernel (Utwórz plik binarny trybu jądra)

Tworzy plik binarny, który może być wykonywany w jądrze systemu Windows. Kod w bieżącym projekcie jest kompilowany i połączony przy użyciu uproszczonego zestawu funkcji języka C++, które są specyficzne dla kodu, który działa w trybie jądra.

## <a name="syntax"></a>Składnia

> **`/kernel`**

## <a name="remarks"></a>Uwagi

Określenie **`/kernel`** opcji nakazuje kompilatorowi i konsolidatorowi rozstrzygnięcie, które funkcje języka są dozwolone w trybie jądra, i upewnić się, że masz wystarczającą moc pozwalającą na uniknięcie niestabilności środowiska uruchomieniowego, która jest unikatowa dla trybu jądra C++. Jest to wykonywane przez Zabroń używania funkcji języka C++, które zakłócają działanie w trybie jądra. Kompilator generuje ostrzeżenia dotyczące funkcji języka C++, które mogą powodować zakłócenia, ale nie mogą być wyłączone.

**`/kernel`** Opcja dotyczy faz kompilatora i konsolidatora kompilacji i jest ustawiana na poziomie projektu. Przekaż **`/kernel`** przełącznik, aby wskazać kompilatorowi, że po konsolidacji powstaje plik binarny, który powinien zostać załadowany do jądra systemu Windows. Kompilator zawęża zakres funkcji języka C++ do podzestawu, który jest zgodny z jądrem.

W poniższej tabeli przedstawiono zmiany zachowania kompilatora, gdy **`/kernel`** jest określony.

| Typ zachowania | **`/kernel`** Domyślnie |
|--|--|
| Obsługa wyjątków C++ | Wyłączona. Wszystkie wystąpienia **`throw`** **`try`** słowa kluczowego and emitują błąd kompilatora (z wyjątkiem specyfikacji wyjątku `throw()` ). Żadne **`/EH`** Opcje nie są zgodne z programem **`/kernel`** , z wyjątkiem **`/EH-`** . |
| RTTI | Wyłączona. Wszystkie wystąpienia **`dynamic_cast`** **`typeid`** słowa kluczowego and emitują błąd kompilatora, chyba że **`dynamic_cast`** jest używany statycznie. |
| `new` i `delete` | Należy jawnie zdefiniować `new()` `delete()` operator or. Kompilator i środowisko uruchomieniowe nie dostarczają definicji domyślnej. |

W [`/GS`](gs-buffer-security-check.md) przypadku użycia opcji można używać niestandardowych konwencji wywoływania, opcji kompilacja i wszystkich optymalizacji **`/kernel`** . W przypadku **`/kernel`** , gdy ta sama semantyka honoruje kompilator, nie ma to żadnego znaczenia. Jeśli chcesz upewnić się **`__forceinline`** , że kwalifikator jest uznawany za honor, musisz upewnić się, że [C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md) ostrzegawczy jest włączony, aby wiedzieć, kiedy określona **`__forceinline`** Funkcja nie jest wbudowana.

Nie istnieje `#pragma` odpowiednik sterowania tą opcją.

Gdy kompilator przeszedł **`/kernel`** przełącznik, wstępnie definiuje makro preprocesora o nazwie `_KERNEL_MODE` i ma wartość **1**. To makro służy do warunkowego kompilowania kodu w zależności od tego, czy środowisko wykonawcze działa w trybie użytkownika, czy na jądrze. Na przykład poniższy kod określa, że `MyNonPagedClass` Klasa powinna znajdować się w segmencie pamięci bez stronicowania, gdy jest kompilowany do wykonywania w trybie jądra.

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

Niektóre z następujących kombinacji architektury docelowej i **`/arch`** opcji powodują wystąpienie błędu, gdy są używane z **`/kernel`** :

- **`/arch:SSE`**, **`/arch:SSE2`** , **`/arch:AVX`** , **`/arch:AVX2`** i **`/arch:AVX512`** nie są obsługiwane w architekturze x86. **`/arch:IA32`** Obsługiwane tylko **`/kernel`** w systemie x86.

- **`/arch:AVX`**, **`/arch:AVX2`** i **`/arch:AVX512`** nie są obsługiwane **`/kernel`** w przypadku wersji x64.

Kompilowanie przy użyciu **`/kernel`** przebiegu również **`/kernel`** do konsolidatora. Oto, jak opcja ma wpływ na zachowanie konsolidatora:

- Łączenie przyrostowe jest wyłączone. W przypadku dodania **`/incremental`** do wiersza polecenia konsolidator emituje ten błąd krytyczny:

   **Błąd krytyczny LNK1295: "/INCREMENTAL" jest niezgodny ze specyfikacją "/KERNEL"; link bez "/INCREMENTAL"**

- Konsolidator sprawdza każdy plik obiektu (lub dowolny składowa archiwalny z bibliotek statycznych), aby sprawdzić, czy mógł zostać skompilowany przy użyciu opcji, ale nie jest **`/kernel`** . Jeśli jakieś wystąpienia spełnią to kryterium, konsolidator nadal pomyślnie łączy się, ale może wydać ostrzeżenie, jak pokazano w poniższej tabeli.

   | Polecenie | **`/kernel`** obiektów | nie- **`/kernel`** obj, MASM obj lub CVTRES obj | Kombinacja **`/kernel`** i **`/kernel`** nieprzywołujące obj zawierały |
   |--|--|--|--|
   | **`link /kernel`** | Tak | Tak | Tak z ostrzeżeniem LNK4257 |
   | **`link`** | Tak | Tak | Tak |

   **LNK4257 łączenie obiektu nie jest kompilowane z/KERNEL; nie można uruchomić obrazu**

**`/kernel`** Opcja i **`/driver`** opcja działają niezależnie. Nie mają one wpływu na siebie.

### <a name="to-set-the-kernel-compiler-option-in-visual-studio"></a>Aby ustawić opcję kompilatora/kernel w programie Visual Studio

1. Otwórz okno dialogowe **strony właściwości** dla projektu. Aby uzyskać więcej informacji, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Configuration Properties**  >  stronę właściwości konfiguracja wiersza polecenia**C/C++**  >  **Command Line** .

1. W polu **dodatkowe opcje** Dodaj *`/kernel`* . Wybierz **przycisk OK** lub **Zastosuj** , aby zapisać zmiany.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora MSVC](compiler-options.md)\
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
