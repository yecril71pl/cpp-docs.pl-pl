---
title: /ENTRY (Symbol punktu wejścia)
ms.date: 11/04/2016
f1_keywords:
- /entry
- VC.Project.VCLinkerTool.EntryPointSymbol
helpviewer_keywords:
- starting address
- -ENTRY linker option
- /ENTRY linker option
- ENTRY linker option
ms.assetid: 26c62ba2-4f52-4882-a7bd-7046a0abf445
ms.openlocfilehash: 80833980b64e8fdd2a2f57b2dc40eb21c784b6f9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232706"
---
# <a name="entry-entry-point-symbol"></a>/ENTRY (Symbol punktu wejścia)

```
/ENTRY:function
```

## <a name="arguments"></a>Argumenty

*funkcyjn*<br/>
Funkcja, która określa zdefiniowany przez użytkownika adres początkowy dla pliku. exe lub DLL.

## <a name="remarks"></a>Uwagi

Opcja/ENTRY określa funkcję punktu wejścia jako adres początkowy dla pliku. exe lub DLL.

Funkcja musi być zdefiniowana do użycia **`__stdcall`** konwencji wywoływania. Parametry i wartość zwracana są zależne od tego, czy program jest aplikacją konsolową, aplikacją systemu Windows lub biblioteką DLL. Zaleca się, aby konsolidator ustawił punkt wejścia w taki sposób, aby Biblioteka uruchomieniowa C została prawidłowo zainicjowana, a konstruktory języka C++ dla obiektów statycznych są wykonywane.

Domyślnie adres początkowy jest nazwą funkcji z biblioteki wykonawczej C. Konsolidator wybiera go zgodnie z atrybutami programu, jak pokazano w poniższej tabeli.

|Nazwa funkcji|Wartość domyślna dla|
|-------------------|-----------------|
|**mainCRTStartup** (lub **wmainCRTStartup**)|Aplikacja, która używa/SUBSYSTEM: CONSOLE; wywołania `main` (lub `wmain` )|
|**WinMainCRTStartup** (lub **wWinMainCRTStartup**)|Aplikacja, która używa/SUBSYSTEM:**Windows**; wywołania `WinMain` (lub `wWinMain` ), które muszą być zdefiniowane do użycia**`__stdcall`**|
|**_DllMainCRTStartup**|BIBLIOTEKA DLL; wywołania `DllMain` , jeśli istnieje, które muszą być zdefiniowane do użycia**`__stdcall`**|

Jeśli opcja [/dll](dll-build-a-dll.md) lub [/Subsystem](subsystem-specify-subsystem.md) nie jest określona, konsolidator wybiera podsystem i punkt wejścia w zależności od tego, czy `main` `WinMain` jest zdefiniowany.

Funkcje `main` , `WinMain` i `DllMain` to trzy formy punktu wejścia zdefiniowanego przez użytkownika.

Podczas tworzenia obrazu zarządzanego funkcja określona dla/ENTRY musi mieć sygnaturę (LPVOID *var1*, DWORD *var2*, LPVOID *var3*).

Aby uzyskać informacje na temat sposobu definiowania własnego `DllMain` punktu wejścia, zobacz [biblioteki DLL i zachowanie biblioteki wykonawczej Visual C++](../run-time-library-behavior.md) .

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij folder **konsolidator** .

1. Kliknij stronę właściwości **Zaawansowane** .

1. Zmodyfikuj właściwość **punktu wejścia** .

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EntryPointSymbol%2A>.

## <a name="see-also"></a>Zobacz także

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[MSVC Opcje konsolidatora](linker-options.md)
