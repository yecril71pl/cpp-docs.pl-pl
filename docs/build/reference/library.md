---
title: BIBLIOTEKA | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- LIBRARY
dev_langs:
- C++
helpviewer_keywords:
- LIBRARY .def file statement
ms.assetid: 1d7ccc92-e088-4ef7-9ef0-25c3862cc051
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0d2fb7e69b0557bf96601666c390b3d59412b5a0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32371167"
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