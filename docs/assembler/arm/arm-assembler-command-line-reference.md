---
title: Dokumentacja wiersza polecenia asemblera ARM
description: Przewodnik referencyjny dotyczący opcji wiersza polecenia asemblera Microsoft ARM.
ms.date: 02/09/2020
ms.assetid: f7b89478-1ab5-4995-8cde-a805f0462c45
ms.openlocfilehash: a63273e8d21e7a28574ec79d62c15f29ee59cd50
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257382"
---
# <a name="arm-assembler-command-line-reference"></a>Dokumentacja wiersza polecenia asemblera ARM

Ten artykuł zawiera informacje o wierszu polecenia dotyczące asemblera ARM firmy Microsoft, **armasm**. **armasm** montuje język asemblera architektury ARMv7 w implementacji firmy Microsoft dla formatu pliku. Konsolidator może połączyć obiekty kodu COFF utworzone przez asemblera ARM i kompilator języka C. Można połączyć ze sobą za pomocą bibliotek obiektów utworzonych przez bibliotekarza.

## <a name="syntax"></a>Składnia

> **`armasm`** [*opcje*] *source_file* *object_file*\
> **`armasm`** [*opcje*] **`-o`** *object_file* *source_file*

### <a name="parameters"></a>Parametry

*opcje*\
Kombinacja zero lub więcej z następujących opcji:

- **`-errors`** *filename*\
   Przekieruj komunikaty Error i Warning do *nazwy pliku*.

- **`-i`** *dir*[ **`;`** <em>dir</em>] \
   Dodaj określone katalogi do ścieżki wyszukiwania dołączania.

- **`-predefine`** \ *dyrektywy*
   Określ dyrektywę SETA, SETL lub SETS, aby wstępnie zdefiniować symbol. \
   Przykład: `armasm.exe -predefine "COUNT SETA 150" source.asm`\
   Aby uzyskać więcej informacji, zobacz [Przewodnik dotyczący odwołania kompilatora ARM armasm](http://infocenter.arm.com/help/topic/com.arm.doc.dui0802b/index.html).

- **`-nowarn`**\
   Wyłącz wszystkie komunikaty ostrzegawcze.

- \ *ostrzeżenia* **`-ignore`**
   Wyłącz określone ostrzeżenie. Aby uzyskać możliwe wartości, zapoznaj się z sekcją dotyczącej ostrzeżeń.

- **`-help`**\
   Drukuj komunikat pomocy wiersza polecenia.

- \ *maszyny* **`-machine`**
   Określ typ maszyny do ustawienia w nagłówku PE.  Możliwe wartości dla *komputera* to: \
   **ARM**— ustawia typ maszyny na IMAGE_FILE_MACHINE_ARMNT. Ta opcja jest wartością domyślną. \
   **Kciuk**— ustawia typ maszyny na IMAGE_FILE_MACHINE_THUMB.

- **`-oldit`**\
   Generuj architektury armv7e bloki IT.  Domyślnie są generowane bloki zgodne z ARMv8.

- **`-via`** *filename*\
   Odczytaj dodatkowe argumenty wiersza polecenia z *pliku filename*.

- **`-16`**\
   Złóż źródło jako 16-bitowe instrukcje dotyczące miniatury.  Ta opcja jest domyślna.

- **`-32`**\
   Złóż źródło jako 32-bitowe instrukcje ARM.

- **`-g`**\
   Generuj informacje o debugowaniu.

- *opcja*`-errorReport:`\
   Ta opcja jest przestarzała. Począwszy od systemu Windows Vista, raportowanie błędów jest kontrolowane przez ustawienia [raportowanie błędów systemu Windows (wer)](/windows/win32/wer/windows-error-reporting) .

*source_file*\
Nazwa pliku źródłowego.

*object_file*\
Nazwa pliku obiektu (wyjściowego).

## <a name="remarks"></a>Uwagi

Poniższy przykład ilustruje sposób używania armasm w typowym scenariuszu. Najpierw użyj armasm do skompilowania pliku źródłowego języka asemblera (. ASM) do pliku obiektu (. obj). Następnie do skompilowania pliku źródłowego (. C), należy użyć polecenia "CL" w kompilatorze języka C, a także określić opcję konsolidatora, aby połączyć plik obiektu ARM.

```cmd
armasm myasmcode.asm -o myasmcode.obj
cl myccode.c /link myasmcode.obj
```

## <a name="see-also"></a>Zobacz też

[Komunikaty diagnostyczne asemblera ARM](../../assembler/arm/arm-assembler-diagnostic-messages.md)\
[Dyrektywy asemblera ARM](../../assembler/arm/arm-assembler-directives.md)
