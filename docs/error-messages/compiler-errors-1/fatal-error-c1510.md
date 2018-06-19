---
title: Błąd krytyczny C1510 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/11/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1510
dev_langs:
- C++
helpviewer_keywords:
- C1510
ms.assetid: 150c827f-9514-41a9-8d7e-82f820749bcb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f39a609e1621dab404ff79e49ade56a88277aa80
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33199356"
---
# <a name="fatal-error-c1510"></a>Błąd krytyczny C1510
Nie można otworzyć zasobu językowego clui.dll  
  
 Kompilator nie można załadować biblioteki DLL zasobów językowych.  
  
Istnieją dwie typowe przyczyny tego problemu. Korzystając z narzędzi i kompilatora 32-bitowy, może zostać wyświetlony ten błąd dla dużych projektów korzystających z więcej niż 2GB pamięci podczas łącze. Możliwe rozwiązanie na 64-bitowe systemy Windows jest korzystanie z macierzystego 64-bitowych lub granic kompilatora i narzędzia do generowania kodu. To korzysta z większą pamięć dostępne dla aplikacji 64-bitowych. Jeśli kompilator 32-bitowy musi być używany, ponieważ został uruchomiony w 32-bitowym systemie, w niektórych przypadkach można zwiększyć ilość dostępnej pamięci, aby konsolidator 3GB. Aby uzyskać więcej informacji, zobacz [dostrajania 4 GB: BCDEdit i Boot.ini](https://msdn.microsoft.com/library/vs/alm/bb613473(v=vs.85).aspx) i [BCDEdit/set increaseuserva](https://msdn.microsoft.com/library/ff542202.aspx) polecenia.  

Typową przyczyną jest uszkodzony lub niekompletnej instalacji programu Visual Studio. W takim przypadku uruchom Instalatora ponownie, aby naprawić lub ponownie zainstalować program Visual Studio.  
  