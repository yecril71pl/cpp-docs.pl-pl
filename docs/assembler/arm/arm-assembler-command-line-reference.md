---
title: Informacje w wierszu polecenia asemblera ARM
ms.date: 08/30/2018
ms.assetid: f7b89478-1ab5-4995-8cde-a805f0462c45
ms.openlocfilehash: f49b59a81fbe5f11c0f219d1e1fe83a4ee811c7a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62162138"
---
# <a name="arm-assembler-command-line-reference"></a>Informacje w wierszu polecenia asemblera ARM

W tym artykule omówiono wiersza polecenia asemblera ARM firmy Microsoft, *armasm*, który kompiluje język asemblera ARMv7 Thumb w implementacji firmy Microsoft z Common Object File Format (COFF). Konsolidator może połączyć COFF kodu za pomocą kod obiektowy, który jest wytwarzany przez asemblera ARM lub przez kompilator języka C, wraz z biblioteki obiektów, które są tworzone przez bibliotekarza.

## <a name="syntax"></a>Składnia

> **armasm** [*opcje*] *sourcefile* *objectfile*
> **armasm** [*opcje*] **-o** *objectfile* *sourcefile*

### <a name="parameters"></a>Parametry

*Opcje*<br/>
Kombinacja zero lub więcej z następujących czynności:

- **-błędy** *nazwy pliku*<br/>
   Przekierowywanie błędach i komunikaty ostrzegawcze do *filename*.

- **-i** *dir*[ **;** <em>dir</em>]<br/>
   Dodaj określonych katalogach na ścieżkę wyszukiwania dołączenia.

- **-wstępnie** *— dyrektywa*<br/>
   Określ dyrektywę SETA, SETL lub zestawy w celu wstępnego zdefiniowania symbolu.<br/>
   Przykład: **armasm.exe — wstępnie source.asm "ZLICZ SETA 150"**<br/>
   Aby uzyskać więcej informacji, zobacz [armasm ARM kompilator podręcznik](http://infocenter.arm.com/help/topic/com.arm.doc.dui0802b/index.html).

- **-nowarn**<br/>
   Wyłącz wszystkie komunikaty ostrzegawcze.

- **-Ignoruj** *ostrzeżenie*<br/>
   Wyłącz określone ostrzeżenie. Możliwe wartości zobacz sekcję dotyczącą ostrzeżenia.

- **-help**<br/>
   Drukuj komunikat pomoc w wierszu polecenia.

- **-machine** *maszyny*<br/>
   Określ typ urządzenia, aby ustawić nagłówek PE.  Możliwe wartości dla *maszyny* są:<br/>
   **ARM**— ustawia typ maszyny IMAGE_FILE_MACHINE_ARMNT. Domyślnie włączone.<br/>
   **THUMB**— ustawia typ maszyny IMAGE_FILE_MACHINE_THUMB.

- **-oldit**<br/>
   Generuj styl ARMv7 bloki IT.  Domyślnie zgodnego z ARMv8 IT bloki są generowane.

- **— za pośrednictwem** *nazwy pliku*<br/>
   Przeczytaj dodatkowe argumenty wiersza polecenia z *filename*.

- **-16**<br/>
   Złóż źródła jako instrukcji Thumb 16-bitowych.  Domyślnie włączone.

- **-32**<br/>
   Złóż źródła jako 32-bitowe instrukcje ARM.

- **-g**<br/>
   Generuj informacje debugowania.

- **-errorReport:** *opcji*<br/>
   Określ asemblera jak wewnętrzne błędy są zgłaszane do firmy Microsoft.  Możliwe wartości dla *opcji* są:<br/>
   **Brak**— nie będą wysyłane raporty.<br/>
   **wiersz**— Monituj użytkownika, aby natychmiast je wysyłać.<br/>
   **kolejka**— monitować użytkownika o wysyłanie raportów przy kolejnym zalogowaniu administratora. Domyślnie włączone.<br/>
   **Wyślij**— Wyślij raporty automatycznie.

*sourcefile*<br/>
Nazwa pliku źródłowego.

*objectfile*<br/>
Nazwa pliku obiektu (dane wyjściowe).

## <a name="remarks"></a>Uwagi

Poniższy przykład pokazuje, jak używać armasm w typowym scenariuszu. Najpierw użyj armasm do utworzenia pliku źródłowego (sam) języka zestawu do pliku obiektu (.obj). Następnie użyj kompilator języka C z wiersza polecenia CL do kompilowania pliku źródłowego (.c) i również określić opcję konsolidatora, aby połączyć pliku obiektu ARM.

**armasm myasmcode.asm -o myasmcode.obj**

**cl myccode.c /link myasmcode.obj**

## <a name="see-also"></a>Zobacz także

[Komunikaty diagnostyczne asemblera ARM](../../assembler/arm/arm-assembler-diagnostic-messages.md)<br/>
[Dyrektywy ARM dotycząca asemblera](../../assembler/arm/arm-assembler-directives.md)<br/>
