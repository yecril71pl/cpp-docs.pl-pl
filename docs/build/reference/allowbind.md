---
title: -ALLOWBIND | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /allowbind
dev_langs:
- C++
helpviewer_keywords:
- ALLOWBIND editbin option
- /ALLOWBIND editbin option
- -ALLOWBIND editbin option
ms.assetid: eaadbb8c-4339-4281-9a75-3a1ce2352ff8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a4cbd5c619b0a9e146adb9a8ec9117f59e01b89d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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