---
title: 'Wskazówki: Kompilowanie C + +/ CLI Program w wierszu polecenia | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: cef41c88-faf9-439d-8423-25aa3f5674dd
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d509bc9890f4fa5ccebbd6ae3d1e3bcb3dbb0d93
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-compiling-a-ccli-program-on-the-command-line"></a>Wskazówki: kompilowanie programu w języku C++/CLI w wierszu polecenia
Tworzenie programów Visual C++, które docelowego środowiska uruchomieniowego języka wspólnego (CLR), a następnie użyj programu .NET Framework i poprowadzi ich kompilację w wierszu polecenia. Visual C++ obsługuje C + +/ języka programowania interfejsu wiersza polecenia, który ma dodatkowe typy i operatory pod kątem model programowania .NET. Aby obejrzeć wprowadzenie do języka C + +/ języka interfejsu wiersza polecenia, zobacz [czysty C++: Hello C + +/ CLI](http://msdn.microsoft.com/magazine/cc163681.aspx). Aby uzyskać ogólne informacje, zobacz [.NET Programowanie w języku C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).  
  
 W tym przewodniku, użyj edytora tekstów do utworzenia podstawowego C + +/ CLI programów i skompiluj go w wierszu polecenia. (Można użyć własnych C + +/ CLI program zamiast wpisywać ten, który jest wyświetlany, lub użyć C + +/ CLI przykładowy kod z innego artykułu pomocy. Ta metoda jest przydatna do tworzenia i testowania małych modułów, które zawierają żadnych elementów interfejsu użytkownika).  
  
> [!NOTE]
>  Umożliwia także programu Visual Studio IDE do kompilacji C + +/ CLI programy. Aby uzyskać więcej informacji, zobacz [wskazówki: kompilowanie programu C++ przeznaczonego dla CLR w Visual Studio](../ide/walkthrough-compiling-a-cpp-program-that-targets-the-clr-in-visual-studio.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Należy zrozumieć podstawowe informacje na temat języka C++.  
  
## <a name="compiling-a-ccli-program"></a>Kompilowania kodu C + +/ CLI programu  
 Poniższe kroki pokazują, jak skompilować C + +/ CLI aplikacja konsolowa, która używa klas .NET Framework.  
  
 Aby włączyć kompilacji C + +/ CLI, należy użyć [/CLR](../build/reference/clr-common-language-runtime-compilation.md) — opcja kompilatora. Kompilator Visual C++ generuje plik .exe, zawierający kod MSIL — lub mieszanego MSIL i kod natywny — oraz łącza do wymaganych bibliotek .NET Framework.  
  
#### <a name="to-compile-a-ccli-application-on-the-command-line"></a>Aby skompilować C + +/ CLI aplikacji w wierszu polecenia  
  
1.  Otwórz **wiersza polecenia dewelopera** okna. Aby uzyskać szczegółowe instrukcje, zobacz [aby otworzyć okno wiersza polecenia dewelopera](../build/building-on-the-command-line.md#developer_command_prompt).  
  
     Poświadczenia administratora może być konieczna pomyślnie skompilowany kod, w zależności od systemu operacyjnego i konfiguracji komputera. Aby uruchomić okno wiersza polecenia jako administrator, kliknij prawym przyciskiem myszy Otwórz menu skrótów wiersza polecenia, a następnie wybierz pozycję **więcej**, **Uruchom jako administrator**.  
  
2.  W wierszu polecenia wprowadź **basicclr.cpp Notatnik**.  
  
     Wybierz **tak** po wyświetleniu monitu można utworzyć pliku.  
  
3.  W programie Notatnik wprowadź następujące wiersze:  
  
    ```  
    int main()  
    {  
        System::Console::WriteLine("This is a C++/CLI program.");  
    }  
    ```  
  
4.  Na pasku menu wybierz **pliku**, **zapisać**.  
  
     Utworzono plik źródłowy języka Visual C++, który używa klasy .NET Framework (<xref:System.Console>) w <xref:System> przestrzeni nazw.  
  
5.  W wierszu polecenia wprowadź **basicclr.cpp/CLR cl**. Cl.exe — kompilator kompiluje kod źródłowy w pliku .obj, który zawiera MSIL, a następnie uruchomi konsolidator, aby wygenerować program wykonywalny o nazwie basicclr.exe.  
  
6.  Aby uruchomić basicclr.exe program, w wierszu polecenia, wpisz **basicclr**.  
  
     Program wyświetla ten tekst i kończy działanie:  
  
    ```Output  
    This is a C++/CLI program.  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)   
 [Kompilowanie programów C/C++](../build/building-c-cpp-programs.md)   
 [Opcje kompilatora](../build/reference/compiler-options.md)