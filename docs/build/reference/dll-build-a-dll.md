---
title: /DLL (Kompilowanie biblioteki DLL)
ms.date: 11/04/2016
f1_keywords:
- /dll
helpviewer_keywords:
- -DLL linker option
- /DLL linker option [C++]
- exporting DLLs [C++], specifying exports
- DLLs [C++], building
- DLL linker option [C++]
ms.assetid: c7685aec-31d0-490f-9503-fb5171a23609
ms.openlocfilehash: 5f7907d659ee3bedc590b88320df03edce005b06
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820510"
---
# <a name="dll-build-a-dll"></a>/DLL (Kompilowanie biblioteki DLL)

```
/DLL
```

## <a name="remarks"></a>Uwagi

Opcja/dll kompiluje bibliotekę DLL jako plik wyjściowy głównego. Biblioteka DLL zawiera zazwyczaj eksportu, które mogą być używane przez inny program. Istnieją trzy metody Określanie eksportów, wymienione w zalecanej kolejności używania:

1. [__declspec(dllexport)](../../cpp/dllexport-dllimport.md) w kodzie źródłowym

1. [EKSPORTY](exports.md) instrukcja w pliku .def

1. [/EXPORT](export-exports-a-function.md) specyfikacji za pomocą polecenia łącza

Program można używać więcej niż jednej metody.

Innym sposobem tworzenia biblioteki DLL jest **biblioteki** instrukcji definicji modułu. Opcje uwzględniają i/dll ze sobą są równoważne **biblioteki** instrukcji.

Nie należy określać tej opcji w środowisku deweloperskim; Ta opcja jest do użytku tylko w wierszu polecenia. Ta opcja jest ustawiona, gdy tworzysz projekt DLL za pomocą Kreatora aplikacji.

Należy pamiętać, że jeśli tworzysz biblioteki importu w krok wstępny, przed utworzeniem usługi .dll, należy przekazać ten sam zestaw plików obiektów podczas tworzenia pliku .dll, jako zakończony powodzeniem w podczas kompilowania biblioteki importowanej.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij przycisk **właściwości konfiguracji** folderu.

1. Kliknij przycisk **ogólne** stronę właściwości.

1. Modyfikowanie **typu konfiguracji** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCPropertySheet.ConfigurationType%2A>.

## <a name="see-also"></a>Zobacz także

[Odwołania konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
