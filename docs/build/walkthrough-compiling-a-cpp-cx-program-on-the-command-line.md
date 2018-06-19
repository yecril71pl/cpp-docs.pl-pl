---
title: 'Wskazówki: Kompilowanie C + +/ CX Program w wierszu polecenia | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 626f5544-69ed-4736-83a9-f11389b371b2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0963f70047ea42893b1169c5da7c614766406280
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32384808"
---
# <a name="walkthrough-compiling-a-ccx-program-on-the-command-line"></a>Wskazówki: kompilowanie programu w języku C++/CX w wierszu polecenia
Można utworzyć programy Visual C++, które docelowego środowiska uruchomieniowego systemu Windows, a następnie utworzyć je w wierszu polecenia. Visual C++ obsługuje rozszerzenia składników dla programu Visual C++ (C + +/ CX), który ma dodatkowe typy i operatory pod kątem modelu programowania środowiska wykonawczego systemu Windows. Można użyć C + +/ CX umożliwia tworzenie aplikacji dla systemu Windows platformy Uniwersalnej systemu Windows Phone 8.1 i Windows desktop. Aby uzyskać więcej informacji, zobacz [A samouczek c + +/ CX](http://msdn.microsoft.com/magazine/dn166929.aspx) i [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md).  
  
 W tym przewodniku, użyj edytora tekstów do utworzenia podstawowego C + +/ CX programów i skompiluj go w wierszu polecenia. (Można użyć własnych C + +/ CX program zamiast wpisywać ten, który jest wyświetlany, lub użyć C + +/ CX przykładowy kod z innego artykułu pomocy. Ta metoda jest przydatna do tworzenia i testowania małych modułów, które zawierają żadnych elementów interfejsu użytkownika).  
  
> [!NOTE]
>  Umożliwia także programu Visual Studio IDE do kompilacji C + +/ CX programy. Ponieważ IDE obejmuje projektowanie, debugowanie, emulacji i obsługa wdrożeń, które nie są dostępne w wierszu polecenia, zalecane jest użycie IDE do tworzenia aplikacji uniwersalnych platformy systemu Windows (UWP). Aby uzyskać więcej informacji, zobacz [tworzenie aplikacji platformy uniwersalnej systemu Windows w języku C++](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Należy zrozumieć podstawowe informacje na temat języka C++.  
  
## <a name="compiling-a-ccx-program"></a>Kompilowania kodu C + +/ CX programu  
 Aby włączyć kompilacji C + +/ CX, należy użyć [/ZW](../build/reference/zw-windows-runtime-compilation.md) — opcja kompilatora. Kompilator Visual C++ generuje plik .exe jest przeznaczony dla środowiska uruchomieniowego systemu Windows, która łączy się wymaganych bibliotek.  
  
#### <a name="to-compile-a-ccx-application-on-the-command-line"></a>Aby skompilować C + +/ CX aplikacji w wierszu polecenia  
  
1.  Otwórz **wiersza polecenia dewelopera** okna. (Na **Start** okna, otwórz **aplikacji**. Otwórz **Visual Studio Tools** folder w używanej wersji programu [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)], a następnie wybierz pozycję **wiersza polecenia dewelopera** skrótów.) Aby uzyskać więcej informacji na temat otworzyć okno wiersza polecenia dewelopera, zobacz [kodu kompilacji C/C++ w wierszu polecenia](../build/building-on-the-command-line.md).  
  
     Poświadczenia administratora może być konieczna pomyślnie skompilowany kod, w zależności od systemu operacyjnego i konfiguracji komputera. Aby uruchomić okno wiersza polecenia jako administrator, otwórz menu skrótów **wiersza polecenia dewelopera** , a następnie wybierz **Uruchom jako administrator**.  
  
2.  W wierszu polecenia wprowadź **basiccx.cpp Notatnik**.  
  
     Wybierz **tak** po wyświetleniu monitu można utworzyć pliku.  
  
3.  W programie Notatnik wprowadź następujące wiersze:  
  
    ```cpp  
    using namespace Platform;  
  
    int main(Platform::Array<Platform::String^>^ args)  
    {  
        Platform::Details::Console::WriteLine("This is a C++/CX program.");  
    }  
  
    ```  
  
4.  Na pasku menu wybierz **pliku**, **zapisać**.  
  
     Utworzono plik źródłowy języka Visual C++, która używa środowiska wykonawczego systemu Windows [przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md) przestrzeni nazw.  
  
5.  W wierszu polecenia wprowadź **cl/ehsc basiccx.cpp /ZW/Link opcji**. Cl.exe — kompilator kompiluje kod źródłowy w postaci pliku obj, a następnie uruchamia konsolidator, aby wygenerować program wykonywalny o nazwie basiccx.exe. ( [/Ehsc](../build/reference/eh-exception-handling-model.md) — opcja kompilatora Określa model obsługi wyjątków języka C++ i [/link](../build/reference/link-pass-options-to-linker.md) flagi określa aplikacji konsoli.)  
  
6.  Aby uruchomić basiccx.exe program, w wierszu polecenia, wpisz **basiccx**.  
  
     Program wyświetla ten tekst i kończy działanie:  
  
    ```Output  
    This is a C++/CX program.  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)   
 [Kompilowanie programów C/C++](../build/building-c-cpp-programs.md)   
 [Opcje kompilatora](../build/reference/compiler-options.md)