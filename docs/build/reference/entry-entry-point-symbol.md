---
title: -ENTRY (Symbol punktu wejścia) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /entry
- VC.Project.VCLinkerTool.EntryPointSymbol
dev_langs:
- C++
helpviewer_keywords:
- starting address
- -ENTRY linker option
- /ENTRY linker option
- ENTRY linker option
ms.assetid: 26c62ba2-4f52-4882-a7bd-7046a0abf445
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 74d7e6e05af98bb3d3175d352fb3d5de1b70b12b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375402"
---
# <a name="entry-entry-point-symbol"></a>/ENTRY (Symbol punktu wejścia)
```  
/ENTRY:function  
```  
  
## <a name="remarks"></a>Uwagi  
 gdzie:  
  
 *Funkcja*  
 Funkcja, która określa początkowy zdefiniowane przez użytkownika adresów dla pliku .exe lub DLL.  
  
## <a name="remarks"></a>Uwagi  
 Opcja/Entry określa funkcję punktu wejścia jako adres początkowy pliku typu .exe lub DLL.  
  
 Funkcja musi być zdefiniowana do używania `__stdcall` konwencji wywoływania. Parametry i wartości zwracanej są zależne od przypadku program aplikacji konsoli, aplikacji systemu windows lub biblioteki DLL. Zalecane jest, aby konsolidator Ustaw punkt wejścia, aby został prawidłowo zainicjowany biblioteki wykonawczej języka C i C++ konstruktorów statycznych obiektów są wykonywane.  
  
 Domyślnie adres początkowy jest nazwę funkcji z biblioteki wykonawcze języka C. Konsolidator zaznacza go zgodnie z atrybutów programu, jak pokazano w poniższej tabeli.  
  
|Nazwa funkcji|Domyślne dla|  
|-------------------|-----------------|  
|**mainCRTStartup** (lub **wmainCRTStartup**)|Aplikacja, która używa opcji; wywołania `main` (lub `wmain`)|  
|**WinMainCRTStartup** (lub **wWinMainCRTStartup**)|Aplikacja, która używa/Subsystem:**WINDOWS**; wywołania `WinMain` (lub `wWinMain`), musi być zdefiniowana do użycia `__stdcall`|  
|**_DllMainCRTStartup**|BIBLIOTEKI DLL; wywołania `DllMain` Jeśli istnieje, który musi być zdefiniowana do użycia `__stdcall`|  
  
 Jeśli [/dll](../../build/reference/dll-build-a-dll.md) lub [/Subsystem](../../build/reference/subsystem-specify-subsystem.md) opcja nie zostanie określona, konsolidator wybiera podsystemu i punktu wejścia w zależności od tego, czy `main` lub `WinMain` jest zdefiniowany.  
  
 Funkcje `main`, `WinMain`, i `DllMain` są trzy rodzaje punktu wejścia użytkownika.  
  
 Podczas tworzenia zarządzanego obrazu, funkcja określone/Entry musi mieć podpis (LPVoid — *var1*, DWORD *var2*, LPVoid — *var3*).  
  
 Aby uzyskać informacje dotyczące sposobu definiowania własnych `DllMain` punktu wejścia, zobacz [biblioteki dll i Visual C++ zachowanie biblioteki wykonawczej](../../build/run-time-library-behavior.md) .  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **konsolidatora** folderu.  
  
3.  Kliknij przycisk **zaawansowane** strony właściwości.  
  
4.  Modyfikowanie **punktu wejścia** właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EntryPointSymbol%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)