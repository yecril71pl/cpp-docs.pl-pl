---
title: modułu .netmodule pliki jako dane wejściowe konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- MSIL linking
- linking [C++], modules
- .netmodules
- modules, Visual C++
ms.assetid: a4bcbe8a-4255-451d-853b-f88cfd82f4e1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bbb2ab74e8c9d0285b9bec2f9979257d89797022
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704568"
---
# <a name="netmodule-files-as-linker-input"></a>Pliki .netmodule — Wejście konsolidatora

Link.exe akceptuje teraz MSIL .obj i modułów .netmodule jako dane wejściowe. Plik wyjściowy utworzony przez konsolidator jest zestawu lub modułu .netmodule z zależności nie czasu wykonywania na każdym .obj lub modułów .netmodule, że dane wejściowe do konsolidatora.

modułów .netmodule są tworzone przez kompilator języka Visual C++ z [/LN (Utwórz moduł MSIL)](../../build/reference/ln-create-msil-module.md) lub przez narzędzie konsolidacji z [/noassembly (Utwórz moduł MSIL)](../../build/reference/noassembly-create-a-msil-module.md). .objs zawsze są tworzone w kompilacji Visual C++. Inne kompilatory Visual Studio, można użyć **/target: module** — opcja kompilatora.

Należy podać do konsolidatora pliku obj. z kompilacji Visual C++, utworzony modułu .netmodule. Przekazywanie modułu .netmodule nie jest obsługiwana, ponieważ **/CLR: pure** i **/CLR: Safe** — opcje kompilatora są używane w programie Visual Studio 2015 i nieobsługiwane w programie Visual Studio 2017 r.

Aby uzyskać informacje na temat sposobu wywoływanie konsolidatora z wiersza polecenia, zobacz [składnia wiersza polecenia konsolidatora](../../build/reference/linker-command-line-syntax.md), [kodu kompilacji C/C++ w wierszu polecenia](../../build/building-on-the-command-line.md), i [Ustawianie ścieżki i zmiennych środowiskowych Kompilacji z wiersza polecenia](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md).

Przekazywanie pliku modułu .netmodule lub dll konsolidator, który został skompilowany przez kompilator języka Visual C++ z **/CLR** może spowodować błąd konsolidatora. Aby uzyskać więcej informacji, zobacz [Wybieranie formatu pliki danych wejściowych modułu .netmodule](../../build/reference/choosing-the-format-of-netmodule-input-files.md).

Konsolidator akceptuje pliki .obj natywnego, a także pliki .obj MSIL skompilowane z **/CLR**. Podczas przekazywania mieszane .objs w tej samej kompilacji, możliwość weryfikacji wynikowego pliku wyjściowego domyślnie będzie równa najniższa możliwość wprowadzania modułów weryfikacji.

Jeśli chcesz aplikacji, które mają zostać zawarte w jednym zestawie aktualnie zainstalowana jest aplikacja, która składa się z dwóch lub więcej zestawów, musi Skompiluj ponownie zestawy, a następnie połącz .objs lub modułów .netmodule do produkcji w jednym zestawie.

Należy określić punkt wejścia przy użyciu [/Entry (Symbol punktu wejścia)](../../build/reference/entry-entry-point-symbol.md) podczas tworzenia obrazu wykonywalnego.

Podczas łączenia się z plikiem obj lub moduł .netmodule MSIL, użyj [opcję/LTCG (Generowanie kodu w czasie Link)](../../build/reference/ltcg-link-time-code-generation.md), w przeciwnym razie jeśli konsolidator napotka MSIL .obj lub moduł .netmodule, będzie uruchamiany ponownie połącz z opcją/LTCG.

Pliki obj lub moduł .netmodule MSIL również mogą być przekazywane do cl.exe.

Wejściowe pliki obj lub moduł .netmodule MSIL nie osadzono zasobów. Zasób jest osadzony w pliku wyjściowym (moduł lub zestaw) z [/assemblyresource (Osadź zarządzany zasób)](../../build/reference/assemblyresource-embed-a-managed-resource.md) — opcja konsolidatora lub **/Resource** — opcja kompilatora w inne kompilatory Visual Studio.

Podczas wykonywania Konsolidacja MSIL, a także nie określisz [opcję/LTCG (Generowanie kodu w czasie Link)](../../build/reference/ltcg-link-time-code-generation.md), zostanie wyświetlony komunikat informacyjny raportowania, czy łącze jest ponownie uruchamiany. Ten komunikat można zignorować, ale w celu podwyższenia wydajności konsolidatora z Konsolidacja MSIL, jawnie określ **opcję/LTCG**.

## <a name="example"></a>Przykład

W kodzie C++ **catch** bloku odpowiadającego **spróbuj** zostanie wywołany dla wyjątku nie ma systemu. Jednak domyślnie CLR opakowuje wyjątki niesystemowych <xref:System.Runtime.CompilerServices.RuntimeWrappedException>. Po utworzeniu zestawu z modułów Visual C++ i z systemem innym niż Visual C++ i ma **catch** bloku kodu C++ do wywołania z odpowiadającymi mu dostawcami **spróbuj** klauzuli podczas **spróbuj**bloku zgłasza wyjątek z systemem innym niż System, należy dodać `[assembly:System::Runtime::CompilerServices::RuntimeCompatibility(WrapNonExceptionThrows=false)]` atrybutu do kodu źródłowego z systemem innym niż C++ modułów.

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

Zmieniając wartość logiczna `WrapNonExceptionThrows` atrybutu, zmodyfikuj możliwość catch wyjątku z systemem innym niż System kodu Visual C++.

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

- [Pliki wejściowe LINK](../../build/reference/link-input-files.md)
- [Opcje konsolidatora](../../build/reference/linker-options.md)
