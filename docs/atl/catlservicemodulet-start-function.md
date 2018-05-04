---
title: Funkcja CAtlServiceModuleT::Start | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- CServiceModule.Start
- CServiceModule::Start
dev_langs:
- C++
helpviewer_keywords:
- Start method
ms.assetid: b5193a23-41bc-42d2-8d55-3eb43dc62238
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: da8d7358c634416941a551c93c6a2772549a3fd2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="catlservicemoduletstart-function"></a>Funkcja CAtlServiceModuleT::Start
Po uruchomieniu usługi **_tWinMain** wywołania **CAtlServiceModuleT::WinMain**, który z kolei wywołuje `CAtlServiceModuleT::Start`.  
  
 `CAtlServiceModuleT::Start` Ustawia tablicę **SERVICE_TABLE_ENTRY** struktur, które mapują każdej usługi do jego uruchamiania funkcji. Ta tablica są następnie przekazywane do funkcji Win32 API [StartServiceCtrlDispatcher](http://msdn.microsoft.com/library/windows/desktop/ms686324). Teoretycznie jednego pliku EXE może obsłużyć wielu usług i Tablica może mieć wielu **SERVICE_TABLE_ENTRY** struktury. Obecnie jednak wygenerowane ATL usługa obsługuje tylko jedną usługę na pliku EXE. W związku z tym tablicy ma pojedynczy wpis, który zawiera nazwę usługi i **_ServiceMain** jako funkcja startowa. **_ServiceMain** jest funkcją statyczny element członkowski `CAtlServiceModuleT` , który odwołuje się funkcja niestatycznego elementu członkowskiego `ServiceMain`.  
  
> [!NOTE]
>  Niepowodzenie **StartServiceCtrlDispatcher** nawiązać sterowania usługami (SCM) manager prawdopodobnie oznacza to, że program nie jest uruchomiony jako usługa. W takim przypadku program wywołuje `CAtlServiceModuleT::Run` bezpośrednio, aby uruchomić program jako serwer lokalny. Aby uzyskać więcej informacji na temat program działa jako serwer lokalny, zobacz [debugowania porady](../atl/debugging-tips.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi](../atl/atl-services.md)   
 [CAtlServiceModuleT::Start](../atl/reference/catlservicemodulet-class.md#start)

