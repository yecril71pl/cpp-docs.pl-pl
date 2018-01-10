---
title: -ZAKRESU | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /RANGE
dev_langs: C++
helpviewer_keywords:
- /RANGE dumpbin option
- -RANGE dumpbin option
ms.assetid: 7eeba266-32be-49cc-a350-96bdf541f98a
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1ccca814a388a458513773247f79cecf87fcdeae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="range"></a>/RANGE
Modyfikuje dane wyjściowe polecenia dumpbin w przypadku użycia z innych opcji dumpbin, takie jak /RAWDATA lub /DISASM.  
  
## <a name="syntax"></a>Składnia  
  
```  
/RANGE:vaMin[,vaMax]  
```  
  
## <a name="flags"></a>Flagi  
 **vaMin**  
 Wirtualny adres, o której chcesz rozpocząć operację dumpbin.  
  
 **vaMax** (opcjonalnie)  
 Wirtualny adres, jaką chcesz zakończyć operację dumpbin. Jeśli nie zostanie określony, dumpbin przejdzie do końca pliku.  
  
## <a name="remarks"></a>Uwagi  
 Aby wyświetlić wirtualne adresy obrazu, należy użyć pliku mapy obrazu (RVA + Base), **/DISASM** lub **/HEADERS** — opcja polecenia dumpbin lub z okna dezasemblacji w debugerze programu Visual Studio.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie **/zakres** jest używane do modyfikowania wyświetlanie **/disasm** opcji. W tym przykładzie wartość początkową jest wyrażone jako liczba dziesiętna i wartości końcowej jest określony jako liczbę szesnastkową.  
  
```  
dumpbin /disasm /range:4219334,0x004061CD t.exe  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje DUMPBIN](../../build/reference/dumpbin-options.md)