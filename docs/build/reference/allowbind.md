---
title: -ALLOWBIND | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /allowbind
dev_langs:
- C++
helpviewer_keywords:
- ALLOWBIND editbin option
- /ALLOWBIND editbin option
- -ALLOWBIND editbin option
ms.assetid: eaadbb8c-4339-4281-9a75-3a1ce2352ff8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: af4a9f3d898d0087f0e8e861ccfe72e4adadb1de
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="allowbind"></a>/ALLOWBIND
Określa, czy biblioteka DLL może być powiązana.  
  
```  
  
/ALLOWBIND[:NO]  
```  
  
## <a name="remarks"></a>Uwagi  
 **/ALLOWBIND** opcji nieco ustawia w nagłówku biblioteki DLL, który wskazuje plikowi Bind.exe obraz może być powiązane. Powiązanie można zezwolić na obraz, aby załadować szybciej, gdy moduł ładujący nie rebase i wykonywać naprawy adresów dla każdej biblioteki DLL, do którego istnieje odwołanie. Nie ma Biblioteka DLL była związana, jeśli został cyfrowo podpisany — powiązanie unieważnia podpis. Powiązanie nie ma efektu Jeśli randomizacji układu przestrzeni adresowej (ASLR) jest włączona dla obrazu przy użyciu **/DYNAMICBASE** w wersjach systemu Windows, która obsługuje ASLR.  
  
 Użyj **/ALLOWBIND:NO** aby zapobiec Bind.exe powiązanie biblioteki DLL.  
  
 Aby uzyskać więcej informacji, zobacz [/ALLOWBIND](../../build/reference/allowbind-prevent-dll-binding.md) — opcja konsolidatora.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje EDITBIN](../../build/reference/editbin-options.md)