---
title: '/Guard: ehcont (Włącz metadane kontynuacji EH)'
description: 'Przewodnik dotyczący opcji kompilatora Microsoft C++/Guard: ehcont.'
ms.date: 06/03/2020
f1_keywords:
- /guard:ehcont
- VC.Project.VCCLCompilerTool.GuardEHContMetadata
helpviewer_keywords:
- /guard:ehcont
- /guard:ehcont compiler option
ms.openlocfilehash: e8775b331440e932efb16148ee15acf1c740cd6e
ms.sourcegitcommit: 7e011c68ca7547469544fac87001a33a37e1792e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84425539"
---
# <a name="guardehcont-enable-eh-continuation-metadata"></a>/Guard: ehcont (Włącz metadane kontynuacji EH)

Włącza generowanie metadanych kontynuacji EH (EHCONT) przez kompilator.

## <a name="syntax"></a>Składnia

> **`/guard:ehcont`**[**`-`**]

## <a name="remarks"></a>Uwagi

**`/guard:ehcont`** Opcja powoduje, że kompilator generuje posortowaną listę względnych adresów wirtualnych (RVA) wszystkich prawidłowych elementów docelowych kontynuacji obsługi wyjątków dla danych binarnych. Jest używany podczas wykonywania `NtContinue` i `SetThreadContext` sprawdzania poprawności wskaźnika instrukcji. Domyślnie program **`/guard:ehcont`** jest wyłączony i musi być jawnie włączony. Aby jawnie wyłączyć tę opcję, użyj **`/guard:ehcont-`** .

Ta **`/guard:ehcont`** opcja jest dostępna w programie Visual Studio 2019 w wersji 16,7 lub nowszej. Funkcja jest obsługiwana w przypadku procesów 64-bitowych na 64-bitowym systemie operacyjnym.

[Technologia kontroli przepływu sterowania (CET)](https://software.intel.com/sites/default/files/managed/4d/2a/control-flow-enforcement-technology-preview.pdf) to oparta na sprzęcie funkcja zabezpieczeń, która chroni przed atakami opartymi na programowaniu (ROP). Zachowuje "stos cieni" dla każdego stosu wywołań, aby wymusić integralność przepływu sterowania.

Gdy dostępne są stosy w tle, aby zapobiec atakom ROP, osoby atakujące przechodzą do korzystania z innych metod korzystania z programu. Jedną z technik, z których mogą korzystać, jest uszkodzenie wartości wskaźnika instrukcji wewnątrz struktury [kontekstu](/windows/win32/api/winnt/ns-winnt-context) . Ta struktura jest przenoszona do wywołań systemowych, które przekierowują wykonywanie wątku, takich jak `NtContinue` , [`RtlRestoreContext`](/windows/win32/api/winnt/nf-winnt-rtlrestorecontext) , i [`SetThreadContext`](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadcontext) . `CONTEXT`Struktura jest przechowywana w pamięci. Uszkodzenie wskaźnika instrukcji, który zawiera, może spowodować, że system wywołuje przekazanie wykonania do adresu kontrolowanego przez osobę atakującą. Obecnie program `NTContinue` można wywołać z dowolnym punktem kontynuacji. Dlatego ważne jest, aby zweryfikować wskaźnik instrukcji po włączeniu stosów w tle.

`RtlRestoreContext`i `NtContinue` są używane w trakcie obsługi wyjątków strukturalnych (SEH), aby odwinięcie do ramki docelowej zawierającej `__except` blok. Wskaźnik instrukcji `__except` bloku nie powinien znajdować się na stosie w tle, ponieważ spowodowałoby to niepowodzenie walidacji wskaźnika instrukcji. **`/guard:ehcont`** Przełącznik kompilatora generuje "tabelę kontynuacji EH". Zawiera posortowaną listę RVA wszystkich prawidłowych elementów docelowych kontynuacji obsługi wyjątków w danych binarnych. `NtContinue`najpierw sprawdza stos cienia dla wskaźnika instrukcji podanej przez użytkownika, a jeśli tam nie znaleziono wskaźnika instrukcji, sprawdza tabelę kontynuacji EH z pliku binarnego zawierającego wskaźnik instrukcji. Jeśli zawiera plik binarny, który nie został skompilowany za pomocą tabeli, można kontynuować, aby zapewnić zgodność z starszymi plikami binarnymi `NtContinue` . Ważne jest odróżnienie od starszych plików binarnych, które nie mają danych EHCONT, oraz plików binarnych zawierających dane EHCONT, ale nie żadnych wpisów w tabeli. Dawniej Zezwalaj na wszystkie adresy wewnątrz pliku binarnego jako prawidłowe cele kontynuacji. Ta ostatnia nie zezwala na żadne adresy w pliku binarnym jako prawidłowy cel kontynuacji.

**`/guard:ehcont`** Opcja musi być przeniesiona do kompilatora i konsolidatora, aby wygenerować RVA docelowy kontynuacji EH dla danych binarnych. Jeśli dane binarne są kompilowane przy użyciu jednego `cl` polecenia, kompilator przekazuje opcję do konsolidatora. Kompilator przekazuje również [**`/guard:cf`**](guard-enable-control-flow-guard.md) opcję do konsolidatora. Jeśli kompilujesz i łączesz oddzielnie, te opcje muszą być ustawione zarówno dla poleceń kompilatora, jak i konsolidatora.

Można połączyć kod skompilowany przy użyciu **`/guard:ehcont`** do bibliotek i plików obiektów skompilowanych bez tego. Konsolidator zwraca błąd krytyczny w jednym z następujących scenariuszy:

- Sekcja kodu ma "lokalne elementy unwind". Aby uzyskać więcej informacji, zobacz nietypowe zakończenie w [instrukcji try-finally](../../cpp/try-finally-statement.md#abnormal-termination).

- Sekcja EH (xdata) zawiera wskaźniki do sekcji kodu, a nie SEH.

- Wskaźniki są przeznaczone dla SEH, ale plik obiektu nie został skompilowany przy użyciu łączenia na poziomie funkcji ([/Gy](gy-enable-function-level-linking.md)) w celu utworzenia COMDAT.

Konsolidator zwraca błąd krytyczny, ponieważ nie może wygenerować metadanych w tych scenariuszach. Oznacza to, że zgłaszanie wyjątku prawdopodobnie spowoduje awarię w czasie wykonywania.

Aby uzyskać informacje dotyczące sekcji SEH w COMDAT, ale nie zostały skompilowane przy użyciu **`/guard:ehcont`** , konsolidator emituje ostrzeżenie **LNK4291**. W takim przypadku konsolidator generuje poprawne, ale ostrożne metadane dla sekcji. Aby zignorować to ostrzeżenie, użyj [/Ignore (Ignoruj określone ostrzeżenia)](ignore-ignore-specific-warnings.md).

Jeśli konsolidator nie może wygenerować metadanych, emituje jeden z następujących błędów:

- **`LNK2046`**`: module contains _local_unwind but was not compiled with /guard:ehcont`

- **`LNK2047`**`: module contains C++ EH or complex EH metadata but was not compiled with /guard:ehcont.`

Aby sprawdzić, czy plik binarny zawiera dane EHCONT, poszukaj następujących elementów w przypadku zatopienia konfiguracji ładowania pliku binarnego:

```cmd
e:\>link /dump /loadconfig CETTest.exe
...
            10417500 Guard Flags
...
                       EH Continuation table present      // EHCONT guard flag present
...
    0000000180018640 Guard EH continuation table
                  37 Guard EH continuation count          // May be 0 if no exception handling is used in the binary. Still counts has having EHCONT data.
...
    Guard EH Continuation Table                           // List of RVAs

          Address
          --------
           0000000180002CF5
           0000000180002F03
           0000000180002F0A
...
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Configuration Properties**  >  stronę właściwości konfiguracja generowania kodu**C/C++**  >  **Code Generation** .

1. Wybierz właściwość **Włącz obsługę metadanych dla kontynuacji EH** .

1. W kontrolce listy rozwijanej wybierz **tak (/Guard: ehcont)** , aby włączyć metadane kontynuacji EH lub **nie (/Guard: ehcont-)** , aby je wyłączyć.

## <a name="see-also"></a>Zobacz też

[/Guard (Włącz ochronę przepływu sterowania)](guard-enable-control-flow-guard.md)\
[Opcje kompilatora MSVC](compiler-options.md)\
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
