---
title: MASM dla wersji x64 (ml64.exe)
ms.date: 08/30/2018
helpviewer_keywords:
- ml64
- ml64.exe
- masm for x64
ms.assetid: 89059103-f372-4968-80ea-0c7f90bb9c91
ms.openlocfilehash: 0404bff54a08988a72fcb0a0c075a4446bf90f48
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62178244"
---
# <a name="masm-for-x64-ml64exe"></a>MASM dla wersji x64 (ml64.exe)

Visual Studio zawiera zarówno 32-bitowych i 64-bitowe wersje hostowanej Microsoft Assembler (MASM) kierowania x64 kodu. Nazwane ml64.exe, to asemblera, który akceptuje x64 języka asemblera. Po wybraniu obciążenia C++ podczas instalacji programu Visual Studio, są zainstalowane narzędzia wiersza polecenia MASM. Narzędzia MASM nie są dostępne do pobrania osobno. Aby uzyskać instrukcje, jak pobrać i zainstalować kopię programu Visual Studio, zobacz [Zainstaluj program Visual Studio](/visualstudio/install/install-visual-studio). Jeśli nie chcesz zainstalować pełne Visual Studio IDE, ale mają tylko narzędzia wiersza polecenia, należy pobrać [Build Tools for Visual Studio 2017](https://go.microsoft.com/fwlink/p/?linkid=875721).

Za pomocą MASM tworzyć kod x64 jest przeznaczony dla w wierszu polecenia, należy użyć wiersz polecenia dla deweloperów x64 obiektów docelowych, które ustawia ścieżkę wymagane i inne zmienne środowiskowe. Aby uzyskać informacje na temat sposobu uruchamiania wiersza polecenia dla deweloperów, zobacz [kodu kompilacji C/C++ w wierszu polecenia](../../build/building-on-the-command-line.md).

Aby uzyskać informacje na temat opcji wiersza polecenia ml64.exe, zobacz [ML i ML64 dotyczące wiersza polecenia](../../assembler/masm/ml-and-ml64-command-line-reference.md).

Asembler wbudowany lub użycie słowa kluczowego ASM nie jest obsługiwana dla x64 lub celów ARM. Do portu usługi x86 kodu tego używa wbudowanego asemblera do x64 lub ARM można przekonwertować kodu C++, użyj funkcje wewnętrzne kompilatora lub utworzyć pliki źródłowe języka asemblera. Kompilator języka Visual C++ obsługuje funkcje wewnętrzne umożliwia postępuj zgodnie z instrukcjami specjalnej funkcji, na przykład uprzywilejowany, bit skanowania i testowania, blokowane i tak dalej, w jak blisko sposób dla wielu platform, jak to możliwe. Aby uzyskać informacji na temat dostępności funkcji wewnętrznych, zobacz [funkcje wewnętrzne kompilatora](../../intrinsics/compiler-intrinsics.md).

## <a name="add-an-assembler-language-file-to-a-visual-c-project"></a>Dodaj plik języka asemblera do projektu Visual C++

System projektu programu Visual Studio obsługuje pliki języka asemblera skompilowanych przy użyciu MASM w projektach C++. Można utworzyć x64 źródło języka asemblera pliki i rozbudowuj je pliki obiektów przy użyciu MASM, która w pełni obsługuje x64. Następnie można połączyć te pliki obiektów kodu C++ wbudowane x64 elementów docelowych. To jest jednym ze sposobów rozwiązywania braku x64 asemblera wbudowanego.

### <a name="to-add-an-assembler-language-file-to-an-existing-visual-c-project"></a>Aby dodać plik języka asemblera do istniejącego projektu Visual C++

1. Wybierz projekt w **Eksploratora rozwiązań**. Na pasku menu wybierz **projektu**, **dostosowania kompilacji**.

1. W **pliki z dostosowywania kompilacji Visual C++** okna dialogowego pole, zaznacz pole wyboru obok pozycji **masm(.targets,.props)**. Wybierz **OK** Aby zapisać swój wybór i zamknąć okno dialogowe.

1. Na pasku menu wybierz **projektu**, **Dodaj nowy element**.

1. W **Dodaj nowy element** okno dialogowe, wybierz opcję **plik C++ (.cpp)** w środkowym okienku. W **nazwa** formant edycji, wprowadź nową nazwę pliku, który ma **.asm** rozszerzenia zamiast .cpp. Wybierz **Dodaj** Dodaj plik do projektu i zamknąć okno dialogowe.

Utwórz kod języka asemblera w pliku .asm, którą dodałeś. Podczas kompilowania rozwiązania asemblera MASM jest wywoływane w celu złożenia plików .asm w pliku obiektu, który jest następnie łączony do projektu. Aby ułatwić dostęp do symboli, deklaruj swoje funkcje asemblera, jak `extern "C"` w kodzie źródłowym C++ zamiast przy użyciu języka C++ nazwę konwencje dekoracji w Twoim języku asembler plików źródłowych.

## <a name="ml64-specific-directives"></a>Dyrektywy specyficzne dla ml64

Następujące dyrektywy specyficzne dla ml64 można użyć w kodzie źródłowym języka asemblera, który jest przeznaczony dla x64:

- [.ALLOCSTACK](../../assembler/masm/dot-allocstack.md)

- [.ENDPROLOG](../../assembler/masm/dot-endprolog.md)

- [.PUSHFRAME](../../assembler/masm/dot-pushframe.md)

- [.PUSHREG](../../assembler/masm/dot-pushreg.md)

- [.SAVEREG](../../assembler/masm/dot-savereg.md)

- [.SAVEXMM128](../../assembler/masm/dot-savexmm128.md)

- [.SETFRAME](../../assembler/masm/dot-setframe.md)

Ponadto [PROC](../../assembler/masm/proc.md) dyrektywa został zaktualizowany do użytku z programem ml64.exe.

## <a name="32-bit-address-mode-address-size-override"></a>Tryb adresu 32-bitowych (adres rozmiar zastąpienie)

MASM emituje zastąpienie rozmiar adresu 0x67, jeśli argument pamięci zawiera 32-bitowych rejestrów. Na przykład poniższe przykłady spowodować zastąpienie rozmiar adresu emitowane:

```asm
mov rax, QWORD PTR [ecx]
mov eax, DWORD PTR [ecx*2+r10d]
mov eax, DWORD PTR [ecx*2+r10d+0100h]
prefetch [eax]
movnti rax, QWORD PTR [r8d]
```

MASM przyjęto założenie, czy jeśli 32-bitowe przesunięcie pojawi się jako argument pamięci, 64-bitowych adresów jest przeznaczony. Obecnie nie jest obsługiwane dla 32-bitowych adresowania za pomocą tych argumentów.

Na koniec mieszanie rozmiary rejestr w ramach operand pamięci, jak pokazano w poniższym kodzie, spowoduje wygenerowanie błędu.

```asm
mov eax, DWORD PTR [rcx*2+r10d]
mov eax, DWORD PTR [ecx*2+r10+0100h]
```

## <a name="see-also"></a>Zobacz także

[Microsoft Macro Assembler — dokumentacja](../../assembler/masm/microsoft-macro-assembler-reference.md)<br/>