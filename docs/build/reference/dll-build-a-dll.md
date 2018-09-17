---
title: -DLL (kompilowanie biblioteki DLL) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /dll
dev_langs:
- C++
helpviewer_keywords:
- -DLL linker option
- /DLL linker option [C++]
- exporting DLLs [C++], specifying exports
- DLLs [C++], building
- DLL linker option [C++]
ms.assetid: c7685aec-31d0-490f-9503-fb5171a23609
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ec5beed66de3834759f35a5021d0155eab0a066e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716836"
---
# <a name="dll-build-a-dll"></a>/DLL (Kompilowanie biblioteki DLL)

```
/DLL
```

## <a name="remarks"></a>Uwagi

Opcja/dll kompiluje bibliotekę DLL jako plik wyjściowy głównego. Biblioteka DLL zawiera zazwyczaj eksportu, które mogą być używane przez inny program. Istnieją trzy metody Określanie eksportów, wymienione w zalecanej kolejności używania:

1. [__declspec(dllexport)](../../cpp/dllexport-dllimport.md) w kodzie źródłowym

1. [EKSPORTY](../../build/reference/exports.md) instrukcja w pliku .def

1. [/EXPORT](../../build/reference/export-exports-a-function.md) specyfikacji za pomocą polecenia łącza

Program można używać więcej niż jednej metody.

Innym sposobem tworzenia biblioteki DLL jest **biblioteki** instrukcji definicji modułu. Opcje uwzględniają i/dll ze sobą są równoważne **biblioteki** instrukcji.

Nie należy określać tej opcji w środowisku deweloperskim; Ta opcja jest do użytku tylko w wierszu polecenia. Ta opcja jest ustawiona, gdy tworzysz projekt DLL za pomocą Kreatora aplikacji.

Należy pamiętać, że jeśli tworzysz biblioteki importu w krok wstępny, przed utworzeniem usługi .dll, należy przekazać ten sam zestaw plików obiektów podczas tworzenia pliku .dll, jako zakończony powodzeniem w podczas kompilowania biblioteki importowanej.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ustawienie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **właściwości konfiguracji** folderu.

1. Kliknij przycisk **ogólne** stronę właściwości.

1. Modyfikowanie **typu konfiguracji** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCPropertySheet.ConfigurationType%2A>.

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)