---
title: -CLRTHREADATTRIBUTE (ustaw atrybut wątku CTR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.CLRThreadAttribute
dev_langs:
- C++
helpviewer_keywords:
- /CLRTHREADATTRIBUTE linker option
- -CLRTHREADATTRIBUTE linker option
ms.assetid: 4907e9ef-5031-446c-aecf-0a0b32fae1e8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b83c3df380b07f125bad8426b9bf18b013b606c8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="clrthreadattribute-set-clr-thread-attribute"></a>/CLRTHREADATTRIBUTE (Ustaw atrybut wątku CTR)
Określ jawnie atrybut wątkowości dla punktu wejścia programu CLR.  
  
## <a name="syntax"></a>Składnia  
  
```  
/CLRTHREADATTRIBUTE:{STA|MTA|NONE}  
```  
  
#### <a name="parameters"></a>Parametry  
 MTA  
 Stosuje atrybut MTAThreadAttribute do punktu wejścia programu.  
  
 BRAK  
 Taka sama jak nieokreślenie /CLRTHREADATTRIBUTE.  Umożliwia wspólnego języka środowiska uruchomieniowego (CLR) Ustaw domyślnego atrybutu wątkowości.  
  
 STA  
 Stosuje atrybut STAThreadAttribute do punktu wejścia programu.  
  
## <a name="remarks"></a>Uwagi  
 Ustawienie atrybutu wątku jest prawidłowa tylko podczas kompilowania .exe, jak ma to wpływ na punkt wejścia wątku głównego.  
  
 Jeśli używasz domyślny punkt wejścia (main lub wmain, na przykład) określanie modelu wątkowości przy użyciu /CLRTHREADATTRIBUTE lub umieszczając wątkowość atrybutu (STAThreadAttribute lub MTAThreadAttribute) w funkcji wpis domyślny.  
  
 Jeśli używasz punktu wejścia innych niż domyślne, określ model wątkowy przy użyciu /CLRTHREADATTRIBUTE lub umieszczając wątkowość atrybutu w funkcji z systemem innym niż domyślny wpis, a następnie określ punkt wejścia innych niż domyślne z [/Entry](../../build/reference/entry-entry-point-symbol.md) .  
  
 Jeśli określony w kodzie źródłowym model wątkowości nie zgadza się z modelem wątków określony za pomocą /CLRTHREADATTRIBUTE, konsolidator zignoruje /CLRTHREADATTRIBUTE i zastosowanie tego modelu wątkowości określona w kodzie źródłowym.  
  
 Konieczne będzie można użyć wątkowość pojedynczej, na przykład, jeśli obiekt COM, który używa wątkowość jednym hostów programu CLR.  Jeśli Twoje CLR programu używa wielowątkowości, go nie może obsługiwać obiektu COM, który używa wątkowość pojedynczej.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozwiń węzeł **właściwości konfiguracji** węzła.  
  
3.  Rozwiń węzeł **konsolidatora** węzła.  
  
4.  Wybierz **zaawansowane** strony właściwości.  
  
5.  Modyfikowanie **atrybut wątku CLR** właściwości.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
1.  Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRThreadAttribute%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)