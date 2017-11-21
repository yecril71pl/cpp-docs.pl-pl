---
title: "Strony właściwości HLSL: Pliki wyjściowe | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.FXCompilerTool.AssemblerOutput
- VC.Project.FXCompilerTool.ObjectFileOutput
- VC.Project.FXCompilerTool.HeaderFileOutput
- VC.Project.FXCompilerTool.VariableName
- VC.Project.FXCompilerTool.AssemblerOutputFile
dev_langs: C++
ms.assetid: c5ba1e72-30de-43eb-a15a-5b0ae58e55c2
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0d41e6f1fd4cf66b45d4f79f4f1b27b3fc4d67a8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
 [Strony właściwości HLSL: Zaawansowane](../ide/hlsl-property-pages-advanced.md)