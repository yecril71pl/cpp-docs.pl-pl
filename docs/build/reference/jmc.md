---
title: / JMC (debugowanie tylko mój kod)
ms.date: 08/20/2018
f1_keywords:
- /JMC
helpviewer_keywords:
- /JMC compiler option [C++]
- Just my code [C++]
- -JMC compiler option [C++]
- User code, debugging
- JMC compiler option [C++]
ms.openlocfilehash: c107ad7107d2a65ed19719933aa127c0557916ce
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57808056"
---
# <a name="jmc-just-my-code-debugging"></a>/ JMC (debugowanie tylko mój kod)

Określa kompilatora obsługę natywnych *tylko mój kod* debugowania w debugerze programu Visual Studio. Ta opcja obsługuje ustawień użytkownika, które umożliwiają programu Visual Studio Przekrocz nad systemu, framework, biblioteki i innymi wywołaniami niespowodowanymi przez użytkownika i zwinąć te wywołania w oknie stosu wywołań. **/JMC** — opcja kompilatora jest dostępna, począwszy od programu Visual Studio 2017 w wersji 15.8.

## <a name="syntax"></a>Składnia

> **/JMC**\[**-**]

## <a name="remarks"></a>Uwagi

Visual Studio [tylko mój kod](/visualstudio/debugger/just-my-code) ustawienia określają, czy debuger programu Visual Studio kroki przez system, framework, biblioteki i innymi wywołaniami niespowodowanymi przez użytkownika. **/JMC** — opcja kompilatora umożliwia obsługę debugowania tylko mój kod w kodzie natywnym języku C++. Gdy **/JMC** jest włączone, kompilator wstawia wywołań funkcji pomocnika, `__CheckForDebuggerJustMyCode`, w prologu funkcji. Funkcja pomocnika zawiera punkty zaczepienia obsługujące operacje kroku tylko mój kod debuger programu Visual Studio. Aby włączyć opcję tylko mój kod w debugerze programu Visual Studio, na pasku menu wybierz **narzędzia** > **opcje**, a następnie ustaw opcję **debugowanie**  >  **Ogólne** > **Włącz tylko mój kod**.

**/JMC** opcja wymaga, że Twój kod łączy do C środowiska uruchomieniowego biblioteki (CRT), który zapewnia `__CheckForDebuggerJustMyCode` funkcji pomocnika. Jeśli projekt nie zawiera linków do CRT, może zostać wyświetlony błąd konsolidatora **LNK2019: Liczba nierozpoznanych symboli zewnętrznych __CheckForDebuggerJustMyCode**. Aby rozwiązać ten problem, połączyć CRT, albo wyłącz **/JMC** opcji.

Domyślnie **/JMC** — opcja kompilatora jest wyłączona. Jednak począwszy od programu Visual Studio 2017 w wersji 15.8, ta opcja jest włączona w większości szablony projektu Visual Studio. Aby jawnie wyłączyć tę opcję, należy użyć **/JMC-** opcji w wierszu polecenia. W programie Visual Studio, Otwórz okno dialogowe strony właściwości projektu i zmień **obsługi tylko mój kod debugowania** właściwość **właściwości konfiguracji** > **C/C++**  >  **Ogólne** stronę właściwości i **nie**.

Aby uzyskać więcej informacji, zobacz [C++ tylko mój kod](/visualstudio/debugger/just-my-code#BKMK_C___Just_My_Code) w [Określ, czy w celu debugowania tylko kodu użytkownika przy użyciu tylko mój kod w programie Visual Studio](/visualstudio/debugger/just-my-code)oraz wpis w blogu zespołu Visual C++ [ogłoszenie C++ tylko mój kod Przechodzenie krok po kroku, w programie Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2018/06/29/announcing-jmc-stepping-in-visual-studio/).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **ogólne** stronę właściwości.

1. Modyfikowanie **obsługi tylko mój kod debugowania** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[MSVC Compiler Options](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
