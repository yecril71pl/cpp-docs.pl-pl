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
ms.openlocfilehash: 25b1c3f83b770dc7b346e83e9675afe423af2516
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465348"
---
# <a name="fatal-error-c1510"></a>Błąd krytyczny C1510
Nie można otworzyć zasobu językowego clui.dll  
  
 Kompilator nie może załadować biblioteki DLL zasobów językowych.  
  
Istnieją dwie typowe przyczyny tego problemu. Korzystając z 32-bitowym kompilatorem i narzędziami, może zostać wyświetlony ten błąd w przypadku dużych projektów, które korzystać z więcej niż 2GB pamięci w czasie łącza. Rozwiązania w 64-bitowych systemach Windows jest użycie natywnego 64-bitowych lub cross kompilator i narzędzia do generowania kodu. To wykorzystuje większy obszar pamięci dostępne dla aplikacji 64-bitowych. Jeśli musisz użyć 32-bitowego kompilatora, ponieważ został uruchomiony w systemie 32-bitowe, w niektórych przypadkach można zwiększyć ilość dostępnej pamięci do konsolidatora do 3GB. Aby uzyskać więcej informacji, zobacz [dostrajania 4 GB: BCDEdit i pliku Boot.ini](https://msdn.microsoft.com/library/vs/alm/bb613473\(v=vs.85\).aspx) i [BCDEdit/set increaseuserva](https://msdn.microsoft.com/library/ff542202.aspx) polecenia.  

Częstą przyczyną jest uszkodzone lub niekompletność instalacji programu Visual Studio. W takim przypadku uruchom Instalatora ponownie, aby naprawić lub zainstalować ponownie program Visual Studio.  
  