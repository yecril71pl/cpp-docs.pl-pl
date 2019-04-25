---
title: Pliki .netmodule — Wejście konsolidatora
ms.date: 11/04/2016
helpviewer_keywords:
- MSIL linking
- linking [C++], modules
- .netmodules
- modules, Visual C++
ms.assetid: a4bcbe8a-4255-451d-853b-f88cfd82f4e1
ms.openlocfilehash: fcba363cff567c69ac0fbd0a541953dfe2c8e910
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320672"
---
# <a name="netmodule-files-as-linker-input"></a>Pliki .netmodule — Wejście konsolidatora

Link.exe akceptuje teraz obj MSIL i modułów .netmodule jako dane wejściowe. Plik wyjściowy, generowany przez konsolidator jest zestaw lub moduł .netmodule z Brak zależności środowiska wykonawczego na każdym .obj lub modułów .netmodule, że dane wejściowe do konsolidatora.

modułów .netmodule są tworzone za pomocą kompilatora MSVC z [/LN (Utwórz moduł MSIL)](ln-create-msil-module.md) lub przez narzędzie konsolidacji z [/noassembly (Utwórz moduł MSIL)](noassembly-create-a-msil-module.md). .objs są zawsze tworzone w kompilacji Visual C++. W przypadku innych kompilatorów programu Visual Studio użyj **/target: module** — opcja kompilatora.

Trzeba przekazać do konsolidatora pliku .obj z kompilacji Visual C++, który utworzony .netmodule. Przekazywanie w .netmodule już nie jest obsługiwana, ponieważ **/CLR: pure** i **/CLR: Safe** opcje kompilatora są przestarzałe w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017.

Aby uzyskać informacje na temat sposobu wywoływanie konsolidatora z wiersza polecenia, zobacz [składnia wiersza polecenia konsolidatora](linking.md), [możesz używać zestawu narzędzi MSVC z wiersza polecenia](../building-on-the-command-line.md), i [Ustawianie ścieżki i zmiennych środowiskowych dla kompilacji z wiersza polecenia](../setting-the-path-and-environment-variables-for-command-line-builds.md).

Przekazywanie pliku modułu .netmodule lub dll do konsolidatora został skompilowany za pomocą kompilatora MSVC z **/CLR** może spowodować błąd konsolidatora. Aby uzyskać więcej informacji, zobacz [Wybieranie formatu plików wejściowych .netmodule](choosing-the-format-of-netmodule-input-files.md).

Program łączący akceptuje pliki .obj natywnego, a także pliki .obj MSIL skompilowany przy użyciu **/CLR**. Przy przekazywaniu mieszane .objs w tej samej kompilacji, możliwość weryfikacji wynikowej pliku wyjściowego domyślnie będzie równa najniższego poziomu możliwość weryfikacji modułów wejściowych.

Jeśli masz już aplikację, która składa się z dwóch lub więcej zestawów i aplikacja muszą być zawarte w jednym zestawie, należy ponownie skompilować zestawy, a następnie połącz .objs lub modułów .netmodule do wyprodukowania jednego zestawu.

Należy określić punkt wejścia przy użyciu [/Entry (Symbol punktu wejścia)](entry-entry-point-symbol.md) podczas tworzenia obrazu wykonywalnego.

Podczas łączenia się z plikiem obj lub moduł .netmodule MSIL, użyj [opcję/LTCG (Generowanie kodu Link-time)](ltcg-link-time-code-generation.md), w przeciwnym razie jeśli konsolidator napotka MSIL .obj lub moduł .netmodule, zostanie ponownie uruchomiony łącze z opcją/LTCG.

Pliki .obj lub moduł .netmodule MSIL również mogą być przekazywane do cl.exe.

Wejściowy pliki .obj lub moduł .netmodule MSIL nie zostały osadzone zasoby. Zasób jest osadzony w pliku danych wyjściowych (moduł lub zestawu) z [linkowany (Osadź zarządzany zasób)](assemblyresource-embed-a-managed-resource.md) — opcja konsolidatora lub **/Resource** — opcja kompilatora w innych kompilatorach Visual Studio.

Podczas przeprowadzania Konsolidacja MSIL, a także nie określisz [opcję/LTCG (Generowanie kodu Link-time)](ltcg-link-time-code-generation.md), zostanie wyświetlony komunikat informacyjny, raportowanie, że łącze jest uruchamiana ponownie. Ten komunikat można zignorować, ale w celu podwyższenia wydajności konsolidatora z Konsolidacja MSIL, jawnie określ **opcję/LTCG**.

## <a name="example"></a>Przykład

W przypadku kodu C++ **catch** odpowiedni blok **spróbuj** zostanie wywołany, dla wyjątku typu innego niż System. Jednak domyślnie środowisko CLR opakowuje niesystemowe wyjątków za pomocą <xref:System.Runtime.CompilerServices.RuntimeWrappedException>. Gdy zestaw jest tworzony z modułów języka Visual C++ i inne niż Visual C++ i chcesz **catch** bloku kodu C++ do wywołania z odpowiadającymi mu dostawcami **spróbuj** klauzuli podczas **spróbuj**bloku wyjątek-System, należy dodać `[assembly:System::Runtime::CompilerServices::RuntimeCompatibility(WrapNonExceptionThrows=false)]` atrybutu do kodu źródłowego dla modułów innego niż C++.

```cpp
// MSIL_linking.cpp
// compile with: /c /clr
value struct V {};

ref struct MCPP {
   static void Test() {
      try {
         throw (gcnew V);
      }
      catch (V ^) {
         System::Console::WriteLine("caught non System exception in C++ source code file");
      }
   }
};

/*
int main() {
   MCPP::Test();
}
*/
```

## <a name="example"></a>Przykład

Zmieniając wartość logiczna `WrapNonExceptionThrows` atrybutu, możesz zmodyfikować możliwość przechwytywanie wyjątku typu innego niż System kodu języka Visual C++.

```cpp
// MSIL_linking_2.cs
// compile with: /target:module /addmodule:MSIL_linking.obj
// post-build command: link /LTCG MSIL_linking.obj MSIL_linking_2.netmodule /entry:MLinkTest.Main /out:MSIL_linking_2.exe /subsystem:console
using System.Runtime.CompilerServices;

// enable non System exceptions
[assembly:RuntimeCompatibility(WrapNonExceptionThrows=false)]

class MLinkTest {
   public static void Main() {
      try {
         MCPP.Test();
      }
      catch (RuntimeWrappedException) {
         System.Console.WriteLine("caught a wrapped exception in C#");
      }
   }
}
```

```Output
caught non System exception in C++ source code file
```

## <a name="see-also"></a>Zobacz także

- [Pliki wejściowe LINK](link-input-files.md)
- [Opcje konsolidatora MSVC](linker-options.md)
