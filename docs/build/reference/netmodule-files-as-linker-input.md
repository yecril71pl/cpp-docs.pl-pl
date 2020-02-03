---
title: .netmodule pliki jako dane wejściowe konsolidatora
description: Opisuje sposób korzystania z mieszanej.obj lub.netmodule pliki jako dane wejściowe konsolidatora podczas tworzenia zestawów .NET.
ms.date: 01/30/2020
helpviewer_keywords:
- MSIL linking
- linking [C++], modules
- .netmodule files
- modules, Visual C++
ms.assetid: a4bcbe8a-4255-451d-853b-f88cfd82f4e1
no-loc:
- obj
- netmodule
- clr
- pure
- safe
ms.openlocfilehash: 83eab25624bdb81ba9191e4efe6a774551502ee0
ms.sourcegitcommit: c4528a7424d35039454f17778baf1b5f98fbbee7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912828"
---
# <a name="opno-locnetmodule-files-as-linker-input"></a>.netmodule pliki jako dane wejściowe konsolidatora

link. exe akceptuje pliki MSIL *`.obj`* i *`.netmodule`* jako dane wejściowe. Plik wyjściowy utworzony przez konsolidatora jest zestawem lub *`.netmodule`* plikiem bez zależności czasu wykonywania na żadnym z *`.obj`* lub *`.netmodule`* plików, które zostały wprowadzone do konsolidatora.

## <a name="remarks"></a>Uwagi

pliki *`.netmodule`* są tworzone przez kompilator MSVC z [/ln (Utwórz moduł MSIL)](ln-create-msil-module.md) lub przez konsolidator przy użyciu [/NOASSEMBLY (Utwórz moduł MSIL)](noassembly-create-a-msil-module.md). pliki *`.obj`* są zawsze tworzone w C++ kompilacji. W przypadku innych kompilatorów programu Visual Studio Użyj opcji " **/target: module** kompilator".

Konsolidator musi przekazywać plik *`.obj`* z C++ kompilacji, która utworzyła *`.netmodule`* . Przekazywanie w *`.netmodule`* nie jest już obsługiwane, ponieważ **/clr:pure** i **/clr:** opcje kompilatorasafesą przestarzałe w programie Visual Studio 2015 i nie są obsługiwane w programie Visual Studio 2017 lub nowszym.

Aby uzyskać informacje na temat wywoływania konsolidatora z wiersza polecenia, zobacz [składnia wiersza polecenia konsolidatora](linking.md), [Używanie zestawu narzędzi MSVC z wiersza polecenia](../building-on-the-command-line.md)i [Ustawianie zmiennych środowiskowych dla kompilacji w wierszu](../setting-the-path-and-environment-variables-for-command-line-builds.md)polecenia.

Przekazywanie *`.netmodule`* lub *`.dll`* pliku do konsolidatora skompilowanego przez kompilator MSVC z **/clr** może spowodować błąd konsolidatora. Aby uzyskać więcej informacji, zobacz [Wybieranie formatu plików wejściowych.netmodule ](choosing-the-format-of-netmodule-input-files.md).

Konsolidator akceptuje zarówno pliki macierzyste *`.obj`* , jak i pliki *`.obj`* MSIL skompilowane przy użyciu **/clr** . W tej samej kompilacji można przekazać pliki mieszane *`.obj`* . Domyślne sprawdzanie poprawności wynikowego pliku wyjściowego jest takie samo jak najniższy możliwy do sprawdzenia Moduł wejściowy.

Można zmienić aplikację, która składa się z co najmniej dwóch zestawów, które mają być zawarte w jednym zestawie. Skompiluj ponownie źródła zestawów, a następnie połącz pliki *`.obj`* lub *`.netmodule`* w celu utworzenia jednego zestawu.

Określ punkt wejścia przy użyciu [/entry (symbol punktu wejścia)](entry-entry-point-symbol.md) podczas tworzenia obrazu wykonywalnego.

Podczas łączenia z plikiem MSIL *`.obj`* lub *`.netmodule`* , użyj [/LTCG (generowanie kodu w czasie konsolidacji)](ltcg-link-time-code-generation.md), w przeciwnym razie, gdy konsolidator napotka *`.obj`* MSIL lub *`.netmodule`* , spowoduje ponowne uruchomienie linku z **/LTCG**. Zobaczysz komunikat informacyjny, że link jest uruchamiany ponownie. Możesz zignorować ten komunikat, ale aby poprawić wydajność konsolidatora, jawnie określ **/LTCG**.

Pliki MSIL *`.obj`* lub *`.netmodule`* można również przekazywać do programu cl. exe.

Wejściowe *`.obj`* MSIL lub pliki *`.netmodule`* nie mogą mieć zasobów osadzonych. Osadź zasoby w module wyjściowym lub pliku zestawu za pomocą [/ASSEMBLYRESOURCE (Osadź zarządzany zasób)](assemblyresource-embed-a-managed-resource.md) opcji konsolidatora. Lub użyj opcji kompilatora **/Resource** w innych kompilatorach programu Visual Studio.

## <a name="examples"></a>Przykłady

W C++ kodzie **`catch`** bloku odpowiadającego **`try`** zostanie wywołana dla wyjątku nie`System`. Jednak domyślnie środowisko CLR otacza wyjątki nie`System` z <xref:System.Runtime.CompilerServices.RuntimeWrappedException>. Gdy C++ zestaw jest tworzony z i bezC++ modułów, i chcesz, aby blok **`catch`** w C++ kodzie był wywoływany z odpowiadającej jej klauzuli **`try`** , gdy blok **`try`** zgłasza wyjątek nie`System`, należy dodać atrybut `[assembly:System::Runtime::CompilerServices::RuntimeCompatibility(WrapNonExceptionThrows=false)]` do kodu źródłowego dlaC++ modułów innych niż moduły.

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

Zmieniając wartość `Boolean` atrybutu `WrapNonExceptionThrows`, można zmodyfikować zdolność C++ kodu do przechwycenia wyjątku nie`System`.

```csharp
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
