---
title: MASM dla wersji x64 (ml64.exe)
ms.date: 08/30/2018
helpviewer_keywords:
- ml64
- ml64.exe
- masm for x64
ms.assetid: 89059103-f372-4968-80ea-0c7f90bb9c91
ms.openlocfilehash: 68f5a14b092109a647e7a81ed6c3fef148a5571b
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397224"
---
# <a name="masm-for-x64-ml64exe"></a>MASM dla wersji x64 (ml64.exe)

Program Visual Studio zawiera zarówno 32-bitowe, jak i 64-bitowe obsługiwane wersje asemblera firmy Microsoft (MASM), aby obsługiwały kod x64. O nazwie ml64. exe jest to asembler, który akceptuje język asemblera x64. Narzędzia wiersza polecenia MASM są instalowane w przypadku wybrania C++ obciążenia podczas instalacji programu Visual Studio. Narzędzia MASM nie są dostępne w oddzielnym pobieraniu. Aby uzyskać instrukcje dotyczące pobierania i instalowania kopii programu Visual Studio, zobacz [Instalowanie programu Visual Studio](/visualstudio/install/install-visual-studio). Jeśli nie chcesz instalować kompletnego środowiska IDE programu Visual Studio, ale potrzebujesz tylko narzędzi wiersza polecenia, Pobierz [narzędzia kompilacji dla programu Visual Studio](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019).

Aby użyć MASM do kompilowania kodu dla obiektów docelowych x64 w wierszu polecenia, należy użyć wiersza polecenia dewelopera dla obiektów docelowych x64, które ustawia wymaganą ścieżkę i inne zmienne środowiskowe. Aby uzyskać informacje na temat sposobu uruchamiania wiersza polecenia dewelopera, zobacz [kompilacja CC++ /Code w wierszu polecenia](../../build/building-on-the-command-line.md).

Aby uzyskać informacje na temat opcji wiersza polecenia ml64. exe, zobacz [informacje dotyczące wiersza polecenia ml i ML64](../../assembler/masm/ml-and-ml64-command-line-reference.md).

Wbudowane asembler lub użycie słowa kluczowego ASM nie jest obsługiwane dla elementów docelowych x64 i ARM. Aby przenieść kod x86, który używa asemblera wbudowanego do architektury x64 lub ARM, Możesz skonwertować swój kod C++na, użyć wewnętrznych kompilatorów lub utworzyć pliki źródłowe języka asemblera. Kompilator firmy C++ Microsoft obsługuje funkcje wewnętrzne, aby umożliwić korzystanie z instrukcji specjalnych, na przykład uprzywilejowanego, skanowania bitowego/testowania, blokowania, i tak dalej, w sposób zbliżony do obsługiwanej przez wiele platform. Aby uzyskać informacje o dostępnych funkcjach wewnętrznych, zobacz [wewnętrzne kompilatory](../../intrinsics/compiler-intrinsics.md).

## <a name="add-an-assembler-language-file-to-a-visual-studio-c-project"></a>Dodawanie pliku pakietu asemblera do projektu programu Visual Studio C++

System projektu programu Visual Studio obsługuje pliki języka asemblera skompilowane przy użyciu MASM w C++ projektach. Można tworzyć pliki źródłowe języka asemblera x64 i kompilować je w plikach obiektów przy użyciu MASM, który obsługuje 64 w pełni. Następnie można połączyć te pliki obiektów z C++ kodem skompilowanym dla celów x64. Jest to jeden ze sposobów na przezwyciężenie braku wbudowanego asemblera x64.

### <a name="to-add-an-assembler-language-file-to-an-existing-visual-studio-c-project"></a>Aby dodać plik programu asemblera do istniejącego projektu programu Visual Studio C++

1. Wybierz projekt w **Eksplorator rozwiązań**. Na pasku menu wybierz **projekt**, a następnie pozycję **dostosowania kompilacji**.

1. W oknie **dialogowym C++ pliki dostosowania kompilacji wizualizacji** zaznacz pole wyboru obok pozycji **MASM (. targets,. props)** . Wybierz **przycisk OK** , aby zapisać wybór i zamknąć okno dialogowe.

1. Na pasku menu wybierz **projekt**, **Dodaj nowy element**.

1. W oknie dialogowym **Dodaj nowy element** wybierz pozycję  **C++ plik (. cpp)** w środkowym okienku. W kontrolce Edycja **nazwy** wprowadź nową nazwę pliku o rozszerzeniu **. asm** zamiast. cpp. Wybierz pozycję **Dodaj** , aby dodać plik do projektu i zamknąć okno dialogowe.

Utwórz kod języka asemblera w pliku. ASM, który został dodany. Podczas kompilowania rozwiązania MASM asembler jest wywoływany, aby złożyć plik. asm do pliku obiektu, który jest następnie połączony z projektem. Aby ułatwić dostęp do symboli, należy zadeklarować funkcje asemblera jako `extern "C"` w C++ kodzie źródłowym, zamiast używać konwencji dekoracji C++ nazw w plikach źródłowych języka asemblera.

## <a name="ml64-specific-directives"></a>Dyrektywy specyficzne dla ml64

W kodzie źródłowym języka asemblera, który jest przeznaczony dla architektury x64, można użyć następujących dyrektyw specyficznych dla ML64:

- [.ALLOCSTACK](../../assembler/masm/dot-allocstack.md)

- [.ENDPROLOG](../../assembler/masm/dot-endprolog.md)

- [.PUSHFRAME](../../assembler/masm/dot-pushframe.md)

- [.PUSHREG](../../assembler/masm/dot-pushreg.md)

- [.SAVEREG](../../assembler/masm/dot-savereg.md)

- [.SAVEXMM128](../../assembler/masm/dot-savexmm128.md)

- [.SETFRAME](../../assembler/masm/dot-setframe.md)

Ponadto dyrektywa [proc](../../assembler/masm/proc.md) została zaktualizowana do użycia z ml64. exe.

## <a name="32-bit-address-mode-address-size-override"></a>32 — tryb adresu bitowego (przesłonięcie rozmiaru adresu)

MASM emituje przesłonięcie rozmiaru adresu 0x67, jeśli argument operacji pamięci zawiera 32-bitowe rejestry. Na przykład następujące przykłady powodują wydawanie przesłania rozmiaru adresu:

```asm
mov rax, QWORD PTR [ecx]
mov eax, DWORD PTR [ecx*2+r10d]
mov eax, DWORD PTR [ecx*2+r10d+0100h]
prefetch [eax]
movnti rax, QWORD PTR [r8d]
```

MASM zakłada, że jeśli przemieszczenie 32-bitowe występuje pojedynczo jako operand pamięci, adres 64-bitowy jest zamierzony. Obecnie nie są obsługiwane adresy 32-bitowe z takimi operandami.

Na koniec mieszanie rozmiarów rejestru w obrębie operandu pamięci, jak pokazano w poniższym kodzie, generuje błąd.

```asm
mov eax, DWORD PTR [rcx*2+r10d]
mov eax, DWORD PTR [ecx*2+r10+0100h]
```

## <a name="see-also"></a>Zobacz także

[Microsoft Macro Assembler — dokumentacja](../../assembler/masm/microsoft-macro-assembler-reference.md)
