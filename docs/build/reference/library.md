---
title: BIBLIOTEKA | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: LIBRARY
dev_langs: C++
helpviewer_keywords: LIBRARY .def file statement
ms.assetid: 1d7ccc92-e088-4ef7-9ef0-25c3862cc051
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 71637c83eda0ee641a4b66d94ba113162baa7bf2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="library"></a>BIBLIOTEKA
Informuje KONSOLIDACJĘ, aby utworzyć biblioteki DLL. W tym samym czasie łącze tworzy biblioteki importowanej, chyba że używana jest plik EXP w kompilacji.  
  
```  
LIBRARY [library][BASE=address]  
```  
  
## <a name="remarks"></a>Uwagi  
 *Biblioteki* argument określa nazwę pliku dll. Można również użyć [/OUT](../../build/reference/out-output-file-name.md) — opcja konsolidatora do określenia nazwy wyjściowego pliku DLL.  
  
 PODSTAWOWYM =*adres* argument ustawia adres podstawowy, używaną do załadowania biblioteki DLL systemu operacyjnego. Ten argument zastępuje domyślną lokalizację biblioteki DLL 0x10000000. Zobacz opis [/BASE](../../build/reference/base-base-address.md) opcji szczegółowe informacje o adres podstawowy.  
  
 Pamiętaj, aby użyć [/dll](../../build/reference/dll-build-a-dll.md) podczas tworzenia biblioteki DLL — opcja konsolidatora.  
  
## <a name="see-also"></a>Zobacz też  
 [Zasady dla instrukcji definicji modułu](../../build/reference/rules-for-module-definition-statements.md)