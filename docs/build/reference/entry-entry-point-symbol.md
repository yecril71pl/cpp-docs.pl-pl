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
ms.openlocfilehash: 0f3604ef75ce10928463c088e423615886555eda
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293215"
---
# <a name="entry-entry-point-symbol"></a>/ENTRY (Symbol punktu wejścia)

```
/ENTRY:function
```

## <a name="arguments"></a>Argumenty

*— Funkcja*<br/>
Funkcja, która określa początkowy zdefiniowanych przez użytkownika adresów dla pliku .exe lub DLL.

## <a name="remarks"></a>Uwagi

Opcja/Entry określa funkcję punktu wejścia jako adres początkowy dla pliku .exe lub DLL.

Funkcja musi być zdefiniowana do użycia `__stdcall` konwencji wywoływania. Parametry i wartości zwracanej są zależne od czy program aplikacji konsoli, aplikacji systemu windows lub biblioteki DLL. Zalecane jest, aby zezwolić konsolidatora, ustaw punkt wejścia, aby biblioteki wykonawczej języka C jest poprawnie zainicjowane i są wykonywane konstruktory C++ dla obiektów statycznych.

Domyślnie adres początkowy jest nazwą funkcji z biblioteki wykonawczej C. Konsolidator zaznacza go zgodnie z atrybutów programu, jak pokazano w poniższej tabeli.

|Nazwa funkcji|Wartość domyślna|
|-------------------|-----------------|
|**mainCRTStartup** (lub **wmainCRTStartup**)|Aplikacja, która używa opcji; wywołania `main` (lub `wmain`)|
|**WinMainCRTStartup** (lub **wWinMainCRTStartup**)|Aplikacja, która używa/Subsystem:**WINDOWS**; wywołania `WinMain` (lub `wWinMain`), musi być zdefiniowana do użycia `__stdcall`|
|**_DllMainCRTStartup**|BIBLIOTEKI DLL; wywołania `DllMain` Jeśli istnieje, które muszą być zdefiniowane do użycia `__stdcall`|

Jeśli [/dll](dll-build-a-dll.md) lub [/Subsystem](subsystem-specify-subsystem.md) opcja nie zostanie określona, konsolidator wybiera punkt podsystemu i zapis w zależności od tego, czy `main` lub `WinMain` jest zdefiniowana.

Funkcje `main`, `WinMain`, i `DllMain` są trzy rodzaje punktu wejścia zdefiniowanych przez użytkownika.

Podczas tworzenia obrazu zarządzanego, funkcja określony do/Entry musi mieć podpis (LPVoid — *var1*, DWORD *var2*, LPVoid — *var3*).

Aby uzyskać informacje na temat sposobu definiowania własnych `DllMain` punktu wejścia, zobacz [bibliotek DLL i Visual C++ zachowanie biblioteki wykonawczej](../run-time-library-behavior.md) .

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **zaawansowane** stronę właściwości.

1. Modyfikowanie **punktu wejścia** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EntryPointSymbol%2A>.

## <a name="see-also"></a>Zobacz także

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
