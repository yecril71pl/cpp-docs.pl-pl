---
title: "C3859 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3859
dev_langs: C++
helpviewer_keywords: C3859
ms.assetid: 40e93b25-4393-4467-90de-035434a665c7
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8a132eb7dbf09421ad5c99249b0208e5f901156b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3859"></a>C3859 błąd kompilatora
zakres wirtualnej pamięci dla PCH jest przekroczony; Skompiluj ponownie, używając opcji wiersza polecenia z "-Zmvalue" lub nowszej  
  
 Prekompilowany nagłówek jest zbyt małe ilości danych, które kompilator próbuje umieścić w tym polu. Użyj **/Zm** flagę kompilatora, aby określić większa wartość dla prekompilowanego pliku nagłówkowego. Aby uzyskać więcej informacji, zobacz [/Zm (Określ Limit pamięci Prekompilowanego nagłówka alokacji)](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md).