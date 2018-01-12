---
title: "Błąd krytyczny C1510 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 04/11/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1510
dev_langs: C++
helpviewer_keywords: C1510
ms.assetid: 150c827f-9514-41a9-8d7e-82f820749bcb
caps.latest.revision: "1"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8d4128580facdc87239d0087fef1cf9eff701854
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1510"></a>Błąd krytyczny C1510
Nie można otworzyć zasobu językowego clui.dll  
  
 Kompilator nie można załadować biblioteki DLL zasobów językowych.  
  
Istnieją dwie typowe przyczyny tego problemu. Korzystając z narzędzi i kompilatora 32-bitowy, może zostać wyświetlony ten błąd dla dużych projektów korzystających z więcej niż 2GB pamięci podczas łącze. Możliwe rozwiązanie na 64-bitowe systemy Windows jest korzystanie z macierzystego 64-bitowych lub granic kompilatora i narzędzia do generowania kodu. To korzysta z większą pamięć dostępne dla aplikacji 64-bitowych. Jeśli kompilator 32-bitowy musi być używany, ponieważ został uruchomiony w 32-bitowym systemie, w niektórych przypadkach można zwiększyć ilość dostępnej pamięci, aby konsolidator 3GB. Aby uzyskać więcej informacji, zobacz [dostrajania 4 GB: BCDEdit i Boot.ini](https://msdn.microsoft.com/library/vs/alm/bb613473(v=vs.85).aspx) i [BCDEdit/set increaseuserva](https://msdn.microsoft.com/library/ff542202.aspx) polecenia.  

Typową przyczyną jest uszkodzony lub niekompletnej instalacji programu Visual Studio. W takim przypadku uruchom Instalatora ponownie, aby naprawić lub ponownie zainstalować program Visual Studio.  
  