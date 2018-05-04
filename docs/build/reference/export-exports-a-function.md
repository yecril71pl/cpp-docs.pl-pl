---
title: -EXPORT (Eksportuje funkcję) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.ExportFunctions
- /export
dev_langs:
- C++
helpviewer_keywords:
- /EXPORT linker option
- EXPORT linker option
- -EXPORT linker option
ms.assetid: 0920fb44-a472-4091-a8e6-73051f494ca0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f366b40e8e40e62f67ec45f3e59ad61eb338c427
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="export-exports-a-function"></a>/EXPORT (Eksportuje funkcję)
```  
/EXPORT:entryname[,@ordinal[,NONAME]][,DATA]  
```  
  
## <a name="remarks"></a>Uwagi  
 Po wybraniu tej opcji można wyeksportować funkcji z programu, aby inne programy można wywołać funkcji. Można również eksportować dane. Eksporty są zazwyczaj definiowane w bibliotece DLL.  
  
 *Nazwa_wpisu* jest nazwa elementu funkcję lub dane, ponieważ jest używane przez program wywołujący. `ordinal` Określa indeks do tabeli eksportu w zakresie od 1 do 65 535; Jeśli nie określisz `ordinal`, LINK przypisuje jeden. **NONAME** — słowo kluczowe eksportuje funkcję tylko jako numer bez *Nazwa_wpisu*.  
  
 **Danych** — słowo kluczowe Określa, że element wyeksportowanego elementu danych. Element danych w programie klienta musi być zadeklarowany za pomocą **extern __declspec(dllimport)**.  
  
 Istnieją trzy metody eksportu definicji, na liście Zalecana kolejność stosowania:  
  
1.  [__declspec(dllexport)](../../cpp/dllexport-dllimport.md) w kodzie źródłowym  
  
2.  [EKSPORTÓW](../../build/reference/exports.md) instrukcji w plik .def  
  
3.  Specyfikacji/Export w poleceniu łącza  
  
 Wszystkie trzy metody może służyć do programu. Gdy łącze tworzy program, który zawiera eksportu, tworzy również biblioteki importowanej, chyba że używana jest plik EXP w kompilacji.  
  
 ŁĄCZE używa dekorowane formularze identyfikatorów. Kompilator decorates identyfikator podczas tworzenia pliku obj. Jeśli *Nazwa_wpisu* określono do konsolidatora w jego bez tworzą (która jest wyświetlana w kodzie źródłowym), łącze próbuje dopasować nazwę. Nie można znaleźć unikatowego dopasowania, LINK generuje komunikat o błędzie. Użyj [DUMPBIN](../../build/reference/dumpbin-reference.md) narzędzia można pobrać [nazwy ozdobione](../../build/reference/decorated-names.md) formę identyfikator, gdy konieczne jest określenie jego do konsolidatora.  
  
> [!NOTE]
>  Nie określaj ozdobione formę identyfikatory języka C, które są zadeklarowane `__cdecl` lub `__stdcall`.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **konsolidatora** folderu.  
  
3.  Kliknij przycisk **wiersza polecenia** strony właściwości.  
  
4.  Typ opcji do **dodatkowe opcje** pole.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)