---
title: "-SEKCJI (Określ atrybuty sekcji) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /section
dev_langs: C++
helpviewer_keywords:
- SECTION linker option
- -SECTION linker option
- section attributes
- /SECTION linker option
ms.assetid: 92b69d81-e421-462e-b46f-7d0dff9b9d16
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e3fd7e844d77b9a92408c0708542a4f8f5edf304
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="section-specify-section-attributes"></a>/SECTION (Określ atrybuty sekcji)
```  
/SECTION:name,[[!]{DEKPRSW}][,ALIGN=#]  
```  
  
## <a name="remarks"></a>Uwagi  
 Opcja/Section zmienia atrybuty sekcji, zastępując zestaw atrybutów, gdy plik .obj sekcji został skompilowany.  
  
 Sekcja przenośny plik wykonywalny (PE) jest w przybliżeniu segment lub zasobów w nowym pliku wykonywalnego (NO). Sekcje zawierają kod lub dane. W przeciwieństwie do segmentów sekcje są bloków pamięci ciągłej z nie ograniczeń rozmiaru. Niektóre sekcje zawierają kod lub dane, które program zadeklarowany i używa bezpośrednio, natomiast pozostałe sekcje zasad zachowania danych są tworzone przez konsolidatora i biblioteki menedżera (lib.exe) i zawierają informacje niezbędne do tego systemu operacyjnego. Aby uzyskać więcej informacji na NE plików Zobacz "Plik wykonywalny Format nagłówka" (Q65122) artykułu bazy wiedzy. Artykuły bazy wiedzy można znaleźć w bibliotece MSDN lub na [http://support.microsoft.com](http://support.microsoft.com).  
  
 Określ dwukropkiem (:) i sekcję *nazwa*. *Nazwa* uwzględniana jest wielkość liter.  
  
 Nie używaj następujących nazw zgodnie z ich może powodować konflikt z standardowe nazwy. Na przykład .sdata jest używana na platformach RISC:  
  
-   .arch  
  
-   .BSS  
  
-   .Data  
  
-   .edata  
  
-   .idata  
  
-   .PData  
  
-   .rdata  
  
-   .reloc  
  
-   rsrc  
  
-   .sbss  
  
-   .sdata  
  
-   .srdata  
  
-   .Text  
  
-   .xdata  
  
 Określ jeden lub więcej atrybutów dla sekcji. Znaki atrybutu, wymienione poniżej, nie jest uwzględniana. Należy określić wszystkie atrybuty, które mają sekcji, aby mieć; znak pominięty atrybut powoduje, że tego atrybutu bit do wyłączenia. Jeśli nie określisz R, P lub E, istniejące odczytu, zapisu lub pliku wykonywalnego stan jest zmieniany.  
  
 Aby odwrócić atrybutu, należy poprzedzić jej znak symbolem wykrzyknika (!). Poniżej przedstawiono znaczenie znaków atrybutu.  
  
|Znak|Atrybut|Znaczenie|  
|---------------|---------------|-------------|  
|E|Wykonanie|Sekcja jest pliku wykonywalnego|  
|R|Odczyt|Zezwala na operacje odczytu danych|  
|W|Write|Zezwala na wykonywanie operacji zapisu na danych|  
|S|Shared|Udostępnia sekcji między wszystkie procesy, które ładują obrazu|  
|D|Discardable|Oznacza sekcji jako discardable|  
|K|Buforowalnej|Oznacza sekcji jako nie buforowalnej|  
|P|Stronicowalnej|Oznacza sekcji jako nie stronicowalnej|  
  
 K i P są specyficzne w tej sekcji odpowiadających im znajdują się w tym sensie, ujemne. Jeśli określisz jeden z nich w sekcji .text (/ sekcji: text, K), nie będzie istnieć różnicy w sekcji flagi, po uruchomieniu [DUMPBIN](../../build/reference/dumpbin-options.md) z [/HEADERS](../../build/reference/headers.md) opcję; już niejawnie był buforowany. Nie można usunąć domyślnego, określ /SECTION:.text! K i DUMPBIN ujawni właściwości sekcji, w tym "Niebuforowane."  
  
 Sekcja w pliku PE, które nie ma E, R lub ustawiona W jest prawdopodobnie nieprawidłowy.  
  
 WYRÓWNAJ *=#*  pozwala określić wartość wyrównania dla określonej sekcji. Zobacz [/ALIGN](../../build/reference/align-section-alignment.md) Aby uzyskać więcej informacji.  
  
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