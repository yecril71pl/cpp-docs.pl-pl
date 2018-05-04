---
title: / APPCONTAINER (aplikacja platformy uniwersalnej systemu Windows/Microsoft sklepu) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 9a432db5-7640-460b-ab18-6f61fa7daf6f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8ca1a3ed5adaada689d374eeb3e67bae6c989e0b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="appcontainer-microsoft-store-app"></a>/ APPCONTAINER (aplikacja ze sklepu firmy Microsoft)
Określa, czy konsolidator tworzy obraz wykonywalny, które muszą być uruchamiane w kontenerze aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
/APPCONTAINER[:NO]  
```  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie /APPCONTAINER jest wyłączone.  
  
 Ta opcja modyfikuje plik wykonywalny, który wskazuje, czy aplikacja musi zostać uruchomiony w środowisku izolacji procesu kontenera aplikacji. Określ /APPCONTAINER dla aplikacji, które muszą działać w środowisku appcontainer — na przykład Windows platformy Uniwersalnej aplikacji lub Windows Phone 8.x aplikacji. (Opcja jest ustawiany automatycznie w programie Visual Studio podczas tworzenia aplikacji uniwersalnych systemu Windows w ramach szablonu.) W przypadku aplikacji klasycznej Określ /APPCONTAINER:NO lub po prostu pominąć opcję.  
  
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