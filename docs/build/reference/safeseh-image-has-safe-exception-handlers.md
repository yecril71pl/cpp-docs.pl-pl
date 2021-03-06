---
title: /SAFESEH (Obraz ma bezpieczną obsługę wyjątków)
ms.date: 11/04/2016
f1_keywords:
- /SAFESEH
helpviewer_keywords:
- /SAFESEH linker option
- -SAFESEH linker option
- SAFESEH linker option
ms.assetid: 7722ff99-b833-4c65-a855-aaca902ffcb7
ms.openlocfilehash: 62784933cbecd4f312c52ae98cab7d232b893f35
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318644"
---
# <a name="safeseh-image-has-safe-exception-handlers"></a>/SAFESEH (Obraz ma bezpieczną obsługę wyjątków)

```
/SAFESEH[:NO]
```

Gdy **opcja/SAFESEH** jest określona, konsolidator generuje tylko obraz jeśli może utworzyć również tabelę obsługi bezpiecznych wyjątków obrazu. Ta tabela określa dla systemu operacyjnego, które programy obsługi wyjątków są prawidłowe dla obrazu.

**/ SAFESEH** jest prawidłowy tylko podczas łączenia do x86 elementów docelowych. **/ SAFESEH** nie jest obsługiwana dla platform, które mają już zapisaną procedurę obsługi wyjątków. Na przykład na x64 i ARM wszystkie obsługi wyjątków są zapisane w PDATA. ML64.exe obsługuje dodawanie adnotacji, które emitują informację strukturalnej obsługi wyjątków (XDATA i PDATA) do obrazu, pozwalając na odpoczynek, dzięki funkcji ml64. Zobacz [MASM x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md) Aby uzyskać więcej informacji.

Jeśli **opcja/SAFESEH** nie jest określona, konsolidator generuje obraz z tabeli obsługi bezpiecznych wyjątków, jeśli wszystkie moduły są zgodne z funkcją obsługi wyjątków bezpiecznych. Jeśli wszystkie moduły nie były zgodne z funkcją obsługi bezpiecznych wyjątków, obraz wynikowy nie będzie zawierać tabeli obsługi bezpiecznych wyjątków. Jeśli [/Subsystem](subsystem-specify-subsystem.md) określa WINDOWSCE lub jedną z opcji EFI_ * konsolidator nie będzie próbował utworzyć obrazu z tabeli obsługi bezpiecznych wyjątków, ponieważ żaden z tych podsystemów ułatwia korzystanie z informacji.

Jeśli **/SAFESEH:NO** jest określony, program łączący wyprodukuje obraz z tabeli obsługi bezpiecznych wyjątków nawet, jeśli wszystkie moduły są zgodne z funkcją obsługi bezpiecznych wyjątków.

Najczęstszą przyczyną, dla której konsolidator nie może wyprodukować obrazu, jest brak zgodności z funkcją obsługi bezpiecznych wyjątków z konsolidatorem, przez jeden lub więcej plików wejściowych (modułów). Częstą przyczyną niezgodności modułu z obsługą bezpiecznych wyjątków jest utworzenie modułu przy użyciu kompilatora poprzednich wersji programu Visual C++.

Funkcję można zarejestrować jako obsługę wyjątków strukturalnych, za pomocą [. SAFESEH](../../assembler/masm/dot-safeseh.md).

Nie istnieje możliwość oznaczenia istniejących danych binarnych jako posiadające obsługę wyjątków bezpiecznych (lub brak obsługi wyjątków); informację na temat obsługi wyjątków bezpiecznych muszą zostać dodane w czasie kompilacji.

Konsolidator posiada możliwość utworzenia tabeli obsługi bezpiecznych wyjątków zależnych od aplikacji przy użyciu biblioteki środowiska uruchomieniowego C. Jeśli łączysz się z [/nodefaultlib](nodefaultlib-ignore-libraries.md) i chcesz uzyskać tabelę obsługi wyjątków bezpiecznych, konieczne podanie ustawień obciążeń struct (na przykład można znaleźć w pliku źródłowym loadcfg.c CRT) zawierający wszystkie wpisy, które są zdefiniowane dla Visual C++. Na przykład:

```
#include <windows.h>
extern DWORD_PTR __security_cookie;  /* /GS security cookie */

/*
* The following two names are automatically created by the linker for any
* image that has the safe exception table present.
*/

extern PVOID __safe_se_handler_table[]; /* base of safe handler entry table */
extern BYTE  __safe_se_handler_count;  /* absolute symbol whose address is
                                           the count of table entries */
typedef struct {
    DWORD       Size;
    DWORD       TimeDateStamp;
    WORD        MajorVersion;
    WORD        MinorVersion;
    DWORD       GlobalFlagsClear;
    DWORD       GlobalFlagsSet;
    DWORD       CriticalSectionDefaultTimeout;
    DWORD       DeCommitFreeBlockThreshold;
    DWORD       DeCommitTotalFreeThreshold;
    DWORD       LockPrefixTable;            // VA
    DWORD       MaximumAllocationSize;
    DWORD       VirtualMemoryThreshold;
    DWORD       ProcessHeapFlags;
    DWORD       ProcessAffinityMask;
    WORD        CSDVersion;
    WORD        Reserved1;
    DWORD       EditList;                   // VA
    DWORD_PTR   *SecurityCookie;
    PVOID       *SEHandlerTable;
    DWORD       SEHandlerCount;
} IMAGE_LOAD_CONFIG_DIRECTORY32_2;

const IMAGE_LOAD_CONFIG_DIRECTORY32_2 _load_config_used = {
    sizeof(IMAGE_LOAD_CONFIG_DIRECTORY32_2),
    0,
    0,
    0,
    0,
    0,
    0,
    0,
    0,
    0,
    0,
    0,
    0,
    0,
    0,
    0,
    0,
    &__security_cookie,
    __safe_se_handler_table,
    (DWORD)(DWORD_PTR) &__safe_se_handler_count
};
```

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **konsolidatora** folderu.

1. Wybierz **wiersza polecenia** stronę właściwości.

1. Wprowadź opcje do **dodatkowe opcje** pole.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
