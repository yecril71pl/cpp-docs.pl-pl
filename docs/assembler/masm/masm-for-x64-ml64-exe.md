---
title: MASM dla x64 (ml64.exe) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ml64
- ml64.exe
- masm for x64
ms.assetid: 89059103-f372-4968-80ea-0c7f90bb9c91
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 437f83c2a226f7b030e1597bab620dcc6869b312
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="masm-for-x64-ml64exe"></a>MASM dla wersji x64 (ml64.exe)

Visual Studio obejmuje zarówno 32-bitowe i 64-bitowe hostowanej wersje MASM do docelowej x64 kodu. Asembler, który akceptuje x64 o nazwie ml64.exe, jest język asemblera. Narzędzia wiersza polecenia MASM są instalowane, po wybraniu obciążenia C++ podczas instalacji programu Visual Studio. Te narzędzia nie są dostępne jako osobny plik do pobrania. Aby pobrać i zainstalować kopię programu Visual Studio, zobacz [https://www.visualstudio.com/](https://www.visualstudio.com/). Jeśli nie chcesz instalować programu Visual Studio IDE, ale mają tylko narzędzia wiersza polecenia, zobacz **Build Tools dla programu Visual Studio 2017** opcja [programu Visual Studio pobiera](https://www.visualstudio.com/downloads/) strony.

Aby skonstruować MASM kod x64 elementów docelowych w wierszu polecenia, należy użyć wiersza polecenia dewelopera dla x64 elementów docelowych, które ustawia wymaganej ścieżki i zmiennych środowiskowych. Aby uzyskać informacje na temat sposobu uruchamiania wiersza polecenia dewelopera, zobacz [kodu kompilacji C/C++ w wierszu polecenia](../../build/building-on-the-command-line.md).

Aby uzyskać informacje na temat opcji wiersza polecenia ml64.exe, zobacz [ML i ML64 dotyczące wiersza polecenia](../../assembler/masm/ml-and-ml64-command-line-reference.md).  
  
Asembler wbudowany lub użyj słowa kluczowego ASM nie jest obsługiwana dla x64 lub obiekty docelowe ARM. Do portu x86 Twojego kodu asemblera wbudowanego tego używa do x64 lub ARM można przekonwertować kodu C++, użyj funkcje wewnętrzne kompilatora lub utworzenia języka asembler plików źródłowych. Kompilator Visual C++ obsługuje funkcje wewnętrzne pozwala używać funkcji specjalne instrukcje, na przykład uprzywilejowane, bit skanowania/testowania, blokowanego i tak dalej, w jak blisko sposób między platformami, jak to możliwe. Aby uzyskać informacje na dostępne funkcje wewnętrzne, zobacz [funkcje wewnętrzne kompilatora](../../intrinsics/compiler-intrinsics.md).  

## <a name="add-an-assembler-language-file-to-a-visual-c-project"></a>Dodaj plik języka asemblera do projektu Visual C++  
  
System projektu programu Visual Studio obsługuje pliki języka asembler skompilowane przy użyciu MASM w projektach C++. Można utworzyć x64 języka asembler źródła plików i je kompilować plikami obiektu przy użyciu MASM, który obsługuje x64 w pełni. Następnie można połączyć te pliki obiektów kodu C++ skompilowany dla x64 elementów docelowych. Jest to można uniknąć braku x64 asemblera wbudowanego.  

### <a name="to-add-an-assembler-language-file-to-an-existing-visual-c-project"></a>Aby dodać plik języka asemblera do istniejącego projektu Visual C++

1. Wybierz projekt **Eksploratora rozwiązań**. Na pasku menu wybierz **projektu**, **kompilacji dostosowania**.

1. W **pliki dostosowania kompilacji C++ Visual** okno dialogowe pola, zaznacz pole wyboru obok pozycji **masm(.targets,.props)**. Wybierz **OK** Aby zapisać wybrane opcje i zamknąć okno dialogowe.

1. Na pasku menu wybierz **projektu**, **Dodaj nowy element**. 

1. W **Dodaj nowy element** okno dialogowe, wybierz opcję **plik C++ (.cpp)** w środkowym okienku. W **nazwa** formantów edycji, wprowadź nową nazwę pliku, który ma **.asm** rozszerzenia zamiast .cpp. Wybierz **Dodaj** Dodaj plik do projektu i zamknąć okno dialogowe.

Utwórz kodu języka asembler w pliku .asm dodane. Podczas kompilowania rozwiązania asemblera MASM jest wywoływane w celu złożenia pliku .asm w pliku obiektu, który jest następnie łączony do projektu. Aby ułatwić dostęp symbol zadeklarować funkcji asemblera jako `extern "C"` w kodu źródłowego języka C++, zamiast przy użyciu języka C++ nazwę konwencje decoration w języku asemblera plików źródłowych.
  
## <a name="ml64-specific-directives"></a>Dyrektywy dotyczące ml64  

Następujące dyrektywy ml64 specyficzne można użyć w kodzie źródłowym języka asembler przeznaczonego x64:  
  
-   [.ALLOCSTACK](../../assembler/masm/dot-allocstack.md)  
  
-   [.ENDPROLOG](../../assembler/masm/dot-endprolog.md)  
  
-   [.PUSHFRAME](../../assembler/masm/dot-pushframe.md)  
  
-   [.PUSHREG](../../assembler/masm/dot-pushreg.md)  
  
-   [.SAVEREG](../../assembler/masm/dot-savereg.md)  
  
-   [.SAVEXMM128](../../assembler/masm/dot-savexmm128.md)  
  
-   [.SETFRAME](../../assembler/masm/dot-setframe.md)  
  
Ponadto [PROC](../../assembler/masm/proc.md) dyrektywa została zaktualizowana do użycia z ml64.exe.  
  
## <a name="32-bit-address-mode-address-size-override"></a>Tryb 32-bitowy adres (adres zastąpienie rozmiar)  

MASM emituje zastąpienie rozmiar 0x67 adres, jeśli argument pamięci zawiera rejestrów 32-bitowych. Na przykład następujące przykłady spowodować zastąpienie rozmiar adres być emitowane:  
  
```MASM  
mov rax, QWORD PTR [ecx]  
mov eax, DWORD PTR [ecx*2+r10d]  
mov eax, DWORD PTR [ecx*2+r10d+0100h]  
prefetch [eax]  
movnti rax, QWORD PTR [r8d]  
```  
  
MASM przyjęto założenie, że 32-bitowe przesunięcie widoczna jako argument pamięci, adresowania 64-bitowych jest przeznaczony. Obecnie nie jest obsługiwane dla 32-bitowego adresowania z tych argumentów operacji.  
  
Na koniec mieszanie rozmiary rejestru w ramach operand pamięci, jak pokazano w poniższym kodzie generuje błąd.  
  
```MASM  
mov eax, DWORD PTR [rcx*2+r10d]  
mov eax, DWORD PTR [ecx*2+r10+0100h]  
```  
  
## <a name="see-also"></a>Zobacz też  

[Microsoft Macro Assembler — dokumentacja](../../assembler/masm/microsoft-macro-assembler-reference.md)