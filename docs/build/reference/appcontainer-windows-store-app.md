---
title: -APPCONTAINER (aplikacja ze Sklepu Windows) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 9a432db5-7640-460b-ab18-6f61fa7daf6f
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 34a1c480e63b5e514e1184d5d3220176b9ba6932
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="appcontainer-windows-store-app"></a>/APPCONTAINER (Aplikacja do sklepu Windows)
Określa, czy konsolidator tworzy obraz wykonywalny, które muszą być uruchamiane w kontenerze aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
/APPCONTAINER[:NO]  
```  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie /APPCONTAINER jest wyłączone.  
  
 Ta opcja modyfikuje plik wykonywalny, który wskazuje, czy aplikacja musi zostać uruchomiony w środowisku izolacji procesu kontenera aplikacji. Określ /APPCONTAINER dla aplikacji, które muszą działać w środowisku appcontainer — na przykład [!INCLUDE[win8_appstore_long](../../build/reference/includes/win8_appstore_long_md.md)] aplikacji. (Opcja jest ustawiany automatycznie w programie Visual Studio po utworzeniu [!INCLUDE[win8_appstore_long](../../build/reference/includes/win8_appstore_long_md.md)] aplikacji z szablonu.) W przypadku aplikacji klasycznej Określ /APPCONTAINER:NO lub po prostu pominąć opcję.  
  
 Opcja /APPCONTAINER została wprowadzona w systemie [!INCLUDE[win8](../../build/reference/includes/win8_md.md)].  
  
### <a name="to-set-this-linker-option-in-visual-studio"></a>Aby ustawić tę opcję konsolidatora w programie Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozwiń węzeł **właściwości konfiguracji** węzła.  
  
3.  Rozwiń węzeł **konsolidatora** węzła.  
  
4.  Wybierz **wiersza polecenia** strony właściwości.  
  
5.  W **dodatkowe opcje**, wprowadź `/APPCONTAINER` lub `/APPCONTAINER:NO`.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)