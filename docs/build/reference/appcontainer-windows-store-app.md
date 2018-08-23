---
title: / APPCONTAINER (aplikacja platformy uniwersalnej systemu Windows/Microsoft Store) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: eab6a9bd8ac37dec250739e3554c370726dce9eb
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42589580"
---
# <a name="appcontainer-microsoft-store-app"></a>/ APPCONTAINER (aplikacja Microsoft Store)
Określa, czy program łączący tworzy obraz wykonywalny, który musi być uruchamiany w kontenerze aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
/APPCONTAINER[:NO]  
```  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie/appcontainer jest wyłączona.  
  
 Opcja ta modyfikuje plik wykonywalny, wskazując, czy aplikacja musi zostać uruchomiony w środowisku izolacji procesu kontenera aplikacji. Określa przełącznik/appcontainer dla aplikacji, które należy uruchomić w środowisku kontenera aplikacji — na przykład, Universal Windows Uniwersalnej systemu Windows Phone 8.x aplikacją lub. (Opcja jest ustawiana automatycznie w programie Visual Studio podczas tworzenia aplikacji Windows Universal z szablonu.) Aplikacji klasycznej należy określić/appcontainer: no lub po prostu pominąć opcję.  
  
 Opcja/appcontainer została wprowadzona w systemie Windows 8.  
  
### <a name="to-set-this-linker-option-in-visual-studio"></a>Aby ustawić tę opcję konsolidatora w programie Visual Studio  
  
1.  Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozwiń **właściwości konfiguracji** węzła.  
  
3.  Rozwiń **konsolidatora** węzła.  
  
4.  Wybierz **wiersza polecenia** stronę właściwości.  
  
5.  W **dodatkowe opcje**, wprowadź `/APPCONTAINER` lub `/APPCONTAINER:NO`.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)