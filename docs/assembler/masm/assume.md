---
title: ZAŁÓŻMY | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- ASSUME
dev_langs:
- C++
helpviewer_keywords:
- ASSUME directive
ms.assetid: cd162070-aee9-4c65-babc-005c6cc73d7c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f8898895d2e107e522fe88dc954146d64e6f62b9
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="assume"></a>ASSUME
Włącza sprawdzanie wartości rejestru.  
  
## <a name="syntax"></a>Składnia  
  
```  
ASSUME segregister:name [[, segregister:name]]...  
ASSUME dataregister:type [[, dataregister:type]]...  
ASSUME register:ERROR [[, register:ERROR]]...  
ASSUME [[register:]] NOTHING [[, register:NOTHING]]...  
```  
  
## <a name="remarks"></a>Uwagi  
 Po `ASSUME` zacznie obowiązywać, asemblera Obserwujący się zmian wartości danego rejestrów. **Błąd** generuje błąd, jeśli jest używany w rejestrze. **NIC** usuwa zarejestrować sprawdzanie błędów. Można łączyć różnego rodzaju założenia w jednej instrukcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)