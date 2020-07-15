---
title: /JMC (Debugowanie Tylko mój kod)
ms.date: 08/20/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.SupportJustMyCode
helpviewer_keywords:
- /JMC compiler option [C++]
- Just my code [C++]
- -JMC compiler option [C++]
- User code, debugging
- JMC compiler option [C++]
ms.openlocfilehash: 7b22a754f9f49564cd7f76c7d1989cd562f70874
ms.sourcegitcommit: 31a443c9998cf5cfbaff00fcf815b133f55b2426
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/14/2020
ms.locfileid: "86373882"
---
# <a name="jmc-just-my-code-debugging"></a>/JMC (Debugowanie Tylko mój kod)

Określa obsługę kompilatora natywnego debugowania *tylko mój kod* w debugerze programu Visual Studio. Ta opcja obsługuje ustawienia użytkownika, które umożliwiają programowi Visual Studio przechodzenie przez system, strukturę, bibliotekę i inne wywołania niezwiązane z użytkownikiem oraz zwijanie tych wywołań w oknie stosu wywołań. Opcja kompilatora **/JMC** jest dostępna w programie Visual Studio 2017 w wersji 15,8.

## <a name="syntax"></a>Składnia

> **/JMC** \[ **-** ]

## <a name="remarks"></a>Uwagi

Ustawienia [tylko mój kod](/visualstudio/debugger/just-my-code) programu Visual Studio określają, czy w debugerze programu Visual Studio są wykonywane kroki dla systemu, struktury, biblioteki i innych wywołań nienależących do użytkownika. Opcja kompilatora **/JMC** umożliwia obsługę debugowania tylko mój kod w kodzie natywnym języka C++. Gdy **/JMC** jest włączona, kompilator wstawia wywołania do funkcji pomocnika, `__CheckForDebuggerJustMyCode` w funkcji Prolog. Funkcja pomocnika udostępnia punkty zaczepienia, które obsługują debuger programu Visual Studio Tylko mój kod operacje krok po kroku. Aby włączyć tylko mój kod w debugerze programu Visual Studio, na pasku menu wybierz opcje **Narzędzia**  >  **Options**, a następnie ustaw opcję **debugowanie**  >  **Ogólne**  >  **Włącz tylko mój kod**.

Opcja **/JMC** wymaga, aby kod łączy się z biblioteką środowiska uruchomieniowego języka C (CRT), która udostępnia `__CheckForDebuggerJustMyCode` funkcję pomocnika. Jeśli projekt nie łączy się z CRT, może pojawić się komunikat o błędzie konsolidatora **LNK2019: nierozpoznany symbol zewnętrzny __CheckForDebuggerJustMyCode**. Aby rozwiązać ten problem, należy połączyć się z CRT lub wyłączyć opcję **/JMC** .

Domyślnie opcja kompilatora **/JMC** jest wyłączona. Jednak począwszy od wersji 15,8 programu Visual Studio 2017 tę opcję można włączyć w większości szablonów projektów programu Visual Studio. Aby jawnie wyłączyć tę opcję, użyj opcji **/JMC-** w wierszu polecenia. W programie Visual Studio Otwórz okno dialogowe strony właściwości projektu i zmień właściwość **Obsługa tylko mój kod debugowanie** we **właściwościach**ogólnych na stronie właściwości konfiguracji  >  **C/C++**  >  **General** na wartość **nie**.

Aby uzyskać więcej informacji, zobacz [c++ tylko mój kod](/visualstudio/debugger/just-my-code#BKMK_C___Just_My_Code) w sekcji [Określanie, czy tylko kod użytkownika ma być debugowany przy użyciu tylko mój kod w programie Visual Studio](/visualstudio/debugger/just-my-code), a wpis w blogu Visual C++ zespołu [ogłaszający C++ tylko mój kod krokowe w programie Visual Studio](https://devblogs.microsoft.com/cppblog/announcing-jmc-stepping-in-visual-studio/).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Configuration Properties**  >  stronę właściwości ogólne**C/C++** właściwości konfiguracji  >  **General** .

1. Zmodyfikuj właściwość **debugowanie tylko mój kod obsługi** .

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
