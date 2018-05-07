---
title: 'Strony właściwości HLSL: Pliki wyjściowe | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.FXCompilerTool.AssemblerOutput
- VC.Project.FXCompilerTool.ObjectFileOutput
- VC.Project.FXCompilerTool.HeaderFileOutput
- VC.Project.FXCompilerTool.VariableName
- VC.Project.FXCompilerTool.AssemblerOutputFile
dev_langs:
- C++
ms.assetid: c5ba1e72-30de-43eb-a15a-5b0ae58e55c2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4fd1dc3ba92201567f24aa84ff8dddcd96798b38
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="hlsl-property-pages-output-files"></a>Strony właściwości HLSL: pliki wyjściowe
Aby skonfigurować następujące właściwości kompilatora HLSL (fxc.exe), użyj jej **pliki wyjściowe** właściwości. Aby uzyskać informacje dotyczące dostępu do **pliki wyjściowe** zobacz stronę właściwości w folderze HLSL [Praca z właściwościami projektu](../ide/working-with-project-properties.md).  
  
## <a name="uielement-list"></a>Lista elementów UI  
 **Nazwa zmiennej nagłówka**  
 Określa nazwę tablicy, która jest używana do zakodowanego kod obiektu HLSL. Tablica znajduje się w pliku nagłówka, który jest wysyłany przez kompilator HLSL. Nazwa pliku nagłówka jest określona przez **nazwę pliku nagłówka** właściwości.  
  
 Ta właściwość odpowiada **/Vn [nazwa]** argumentu wiersza polecenia.  
  
 **Nazwa pliku nagłówka**  
 Określa nazwę pliku nagłówka, który jest wysyłany przez kompilator HLSL. Nagłówek zawiera HLSL kod obiektu, który jest zakodowany w tablicy. Nazwa tablicy jest określona przez **nazwa zmiennej nagłówka** właściwości.  
  
 Ta właściwość odpowiada **/Fh [nazwa]** argumentu wiersza polecenia.  
  
 **Nazwa pliku obiektu**  
 Określa nazwę pliku obiektu, który jest wysyłany przez kompilator HLSL. Domyślna wartość to **.cso % (nazwa pliku) $(OutDir)**.  
  
 Ta właściwość odpowiada **/Fo [nazwa]** argumentu wiersza polecenia.  
  
 **Wynik zestawów**  
 **Listowanie tylko zestawów (/ Fc)** do właśnie instrukcji języka zestawu wyjściowego. **Zestaw kodu i wartości szesnastkowej (/ Fx)** do wyjściowego zarówno instrukcji języka zestawu i odpowiedni kod operacji w formacie szesnastkowym. Domyślnie wyświetlana jest danych wyjściowych.  
  
 **Plik wyjściowy asemblera**  
 Określa nazwę pliku listy zestawu, który jest wysyłany przez kompilator HLSL.  
  
 Ta właściwość odpowiada **/Fc [nazwa]** i **/Fx [nazwa]** argumenty wiersza polecenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Strony właściwości HLSL](../ide/hlsl-property-pages.md)   
 [Strony właściwości HLSL: Ogólne](../ide/hlsl-property-pages-general.md)   
 [Strony właściwości HLSL: zaawansowane](../ide/hlsl-property-pages-advanced.md)