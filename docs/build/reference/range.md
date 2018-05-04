---
title: -ZAKRESU | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /RANGE
dev_langs:
- C++
helpviewer_keywords:
- /RANGE dumpbin option
- -RANGE dumpbin option
ms.assetid: 7eeba266-32be-49cc-a350-96bdf541f98a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d06d699500ba3ea441af61a2e2a5a0da3f96903a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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