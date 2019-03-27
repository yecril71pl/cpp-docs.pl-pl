---
title: 'Strony właściwości HLSL: Pliki wyjściowe'
ms.date: 11/04/2016
f1_keywords:
- VC.Project.FXCompilerTool.AssemblerOutput
- VC.Project.FXCompilerTool.ObjectFileOutput
- VC.Project.FXCompilerTool.HeaderFileOutput
- VC.Project.FXCompilerTool.VariableName
- VC.Project.FXCompilerTool.AssemblerOutputFile
ms.assetid: c5ba1e72-30de-43eb-a15a-5b0ae58e55c2
ms.openlocfilehash: 6ee8042fccf2e0b635535a77d9c9a6bc68bd9999
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823240"
---
# <a name="hlsl-property-pages-output-files"></a>Strony właściwości HLSL: Pliki wyjściowe

Aby skonfigurować następujące właściwości kompilator HLSL (fxc.exe), użyj jej **pliki wyjściowe** właściwości. Aby uzyskać informacje o tym, jak uzyskać dostęp do **pliki wyjściowe** zobacz stronę właściwości w folderze HLSL [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

## <a name="uielement-list"></a>Lista elementów UI

- **Nazwa zmiennej nagłówka**

   Określa nazwę tablicy, która jest używana do zakodowanego kod obiektowy HLSL. Tablica jest zawarty w pliku nagłówkowym, który jest wysyłany przez kompilator HLSL. Nazwa pliku nagłówkowego jest określona przez **nazwa pliku nagłówkowego** właściwości.

Ta właściwość odnosi się do **/Vn [nazwa]** argument wiersza polecenia.

- **Nazwa pliku nagłówkowego**

   Określa nazwę pliku nagłówkowego, który jest wysyłany przez kompilator HLSL. Nagłówek zawiera kod obiektowy HLSL, który jest kodowany na tablicę. Nazwa tablicy jest określona przez **nazwa zmiennej nagłówka** właściwości.

Ta właściwość odnosi się do **/Fh [nazwa]** argument wiersza polecenia.

- **Nazwa pliku obiektu**

   Określa nazwę pliku obiektu, który jest wysyłany przez kompilator HLSL. Domyślna wartość to **.cso % (nazwa_pliku) $(OutDir)**.

Ta właściwość odnosi się do **/Fo [nazwa]** argument wiersza polecenia.

- **Produkt wyjściowy asemblera**

   **Listowanie tylko zestawów (/ Fc)** służący do wypełniania wyjściowego po prostu instrukcje języka asemblera. **Kodem asemblera i zapisem szesnastkowym (/ Fx)** służący do wypełniania wyjściowego języka zestawu instrukcji i odpowiedni kod operacji w formacie szesnastkowym. Domyślnie wyświetlana jest dane wyjściowe.

- **Plik wyjściowy zestawu**

   Określa nazwę plik listingu asemblera, który jest wysyłany przez kompilator HLSL.

   Ta właściwość odnosi się do **/Fc [name]** i **/Fx [name]** argumenty wiersza polecenia.

## <a name="see-also"></a>Zobacz także

[Strony właściwości HLSL](hlsl-property-pages.md)<br>
[Strony właściwości HLSL: Ogólne](hlsl-property-pages-general.md)<br>
[Strony właściwości HLSL: Zaawansowane](hlsl-property-pages-advanced.md)