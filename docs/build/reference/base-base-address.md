---
title: -BASE (adres podstawowy) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /base
- VC.Project.VCLinkerTool.BaseAddress
dev_langs: C++
helpviewer_keywords:
- base addresses [C++]
- programs [C++], preventing relocation
- semicolon [C++], specifier
- -BASE linker option
- key address size
- environment variables [C++], LIB
- programs [C++], base address
- LIB environment variable
- BASE linker option
- DLLs [C++], linking
- /BASE linker option
- '@ symbol for base address'
- executable files [C++], base address
- at sign symbol for base address
ms.assetid: 00b9f6fe-0bd2-4772-a69c-7365eb199069
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9ddf399757d881484817be676ca3077b4fc21709
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="base-base-address"></a>/BASE (Adres podstawowy)
```  
/BASE:{address[,size] | @filename,key}  
```  
  
 / PODSTAWOWEJ opcji ustawia adres podstawowy dla programu, zastępowanie domyślną lokalizację pliku .exe lub DLL. Domyślny adres podstawowy plik .exe jest 0x400000 dla 32-bitowych obrazów lub 0x140000000 dla 64-bitowych obrazów. Dla biblioteki DLL domyślny adres podstawowy jest 0x10000000 dla 32-bitowych obrazów lub 0x180000000 dla 64-bitowych obrazów. W systemach operacyjnych, które nie obsługują randomizacji układu przestrzeni adresowej (ASLR) lub gdy opcja No została ustawiona system operacyjny najpierw próbuje załadować programu w jego określonego lub domyślnego adres podstawowy. Jeśli wystarczającą ilość miejsca jest niedostępne w nie, system przenosi program. Aby zapobiec relokacji, użyj [/FIXED](../../build/reference/fixed-fixed-base-address.md) opcji.  
  
 Konsolidator generuje błąd, jeśli *adres* nie jest wielokrotnością 64 KB. Opcjonalnie można określić rozmiaru program; konsolidator wygeneruje ostrzeżenie, jeśli program nie mieści się w podany rozmiar.  
  
 W wierszu polecenia inny sposób, aby określić adres podstawowy jest przy użyciu pliku odpowiedzi adres podstawowy. Adres podstawowy plik odpowiedzi jest plik tekstowy zawierający adresy podstawowy i opcjonalnie rozmiary wszystkich bibliotek DLL programu, użyje i tekst Unikatowy klucz dla każdego adresu podstawowego. Aby określić adres podstawowy przy użyciu pliku odpowiedzi, należy użyć znaku (@) i nazwa pliku odpowiedzi *filename*, a następnie przecinek, a następnie `key` wartość dla adresu podstawowego do użycia w pliku. Wyszukuje konsolidator *filename* albo na określonej ścieżce, lub jeśli nie określono ścieżki, w katalogach określonych w zmiennej środowiskowej LIB. Każdy wiersz w *filename* reprezentuje jeden biblioteki DLL i ma następującą składnię:  
  
```  
  
key address [size] ;comment  
```  
  
 `key` Ciąg znaków alfanumerycznych i nie jest uwzględniana wielkość liter. Zazwyczaj jest to nazwa biblioteki DLL, ale nie muszą być. `key` Następuje podstawowej *adres* w notacji języka C, szesnastkową lub dziesiętną i opcjonalnie maksymalny `size`. Wszystkie trzy argumenty są oddzielone spacjami lub kart. Konsolidator wygeneruje ostrzeżenie, jeśli określony `size` jest mniejsza niż wirtualnej przestrzeni adresowej wymagane przez program. A `comment` określono za pomocą średnika (;) i może być na tym samym lub w oddzielnym wierszu. Konsolidator ignoruje wszystkie po średniku do końca wiersza. W tym przykładzie przedstawiono część tego pliku:  
  
```  
main   0x00010000    0x08000000    ; for PROJECT.exe  
one    0x28000000    0x00100000    ; for DLLONE.DLL  
two    0x28100000    0x00300000    ; for DLLTWO.DLL  
```  
  
 Jeśli plik, który zawiera te wiersze po wywołaniu DLLS.txt następujące przykładowe polecenie stosuje się te informacje:  
  
```  
link dlltwo.obj /dll /base:@dlls.txt,two  
```  
  
## <a name="remarks"></a>Uwagi  
 Ze względów bezpieczeństwa firma Microsoft zaleca używasz [/DYNAMICBASE](../../build/reference/dynamicbase-use-address-space-layout-randomization.md) opcji zamiast określania adresu podstawowego dla Twojego plików wykonywalnych. Spowoduje to wygenerowanie obrazu wykonywalnego, który może być losowo przebazowanych w czasie obciążenia za pomocą funkcji adres miejsca układu losowe (ASLR) systemu Windows. Opcja /DYNAMICBASE jest domyślnie.  
  
 Innym sposobem, aby ustawić adres podstawowy jest przy użyciu *podstawowej* argumentu w [nazwa](../../build/reference/name-c-cpp.md) lub [biblioteki](../../build/reference/library.md) instrukcji. /BASE i [/dll](../../build/reference/dll-build-a-dll.md) razem opcje są równoważne **biblioteki** instrukcji.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Rozwiń węzeł **konsolidatora** folderu.  
  
3.  Wybierz **zaawansowane** strony właściwości.  
  
4.  Modyfikowanie **adresu podstawowego** właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.BaseAddress%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)