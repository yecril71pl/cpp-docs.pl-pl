---
title: Ostrzeżenie LNK4222 narzędzi konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4222
dev_langs:
- C++
helpviewer_keywords:
- LNK4222
ms.assetid: b7bb1794-41fb-4c83-b9b0-59c0d786a7da
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 359af4c4d3b1079b2d56f108bff0ee1488ea71f9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4222"></a>Ostrzeżenie LNK4222 narzędzi konsolidatora
do wyeksportowanego symbolu "symbol" nie należy przypisywać liczby porządkowej  
  
 Następujących symboli nie powinien zostać wyeksportowany według liczby porządkowej:  
  
-   `DllCanUnloadNow`  
  
-   `DllGetClassObject`  
  
-   `DllGetClassFactoryFromClassString`  
  
-   `DllInstall`  
  
-   `DllRegisterServer`  
  
-   `DllRegisterServerEx`  
  
-   `DllUnregisterServer`  
  
 Te funkcje zawsze znajdują się według nazwy, za pomocą `GetProcAddress`. Konsolidator ostrzega o tym rodzaj eksportu jest ponieważ mogłaby ona spowodować większy obraz. Może się to zdarzyć, jeśli zakres z liczby porządkowej eksportu jest duży z względnie mało eksportu. Na przykład  
  
```  
EXPORTS  
   DllGetClassObject   @1  
   MyOtherAPI      @100  
```  
  
 wymagają 100 gniazd tabeli eksportu adres 98 ich po prostu wypełniacza (2 – 99). Z drugiej strony  
  
```  
EXPORTS  
   DllGetClassObject  
   MyOtherAPI      @100  
```  
  
 wymaga dwóch miejsc. (Należy pamiętać, że można również wyeksportować z [/EXPORT](../../build/reference/export-exports-a-function.md) — opcja konsolidatora.)