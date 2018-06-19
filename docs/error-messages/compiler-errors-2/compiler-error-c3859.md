---
title: C3859 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3859
dev_langs:
- C++
helpviewer_keywords:
- C3859
ms.assetid: 40e93b25-4393-4467-90de-035434a665c7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d2f8c51f25c09881e10e980276fc2035a6a70aed
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33272308"
---
# <a name="compiler-error-c3859"></a>C3859 błąd kompilatora
zakres wirtualnej pamięci dla PCH jest przekroczony; Skompiluj ponownie, używając opcji wiersza polecenia z "-Zmvalue" lub nowszej  
  
 Prekompilowany nagłówek jest zbyt małe ilości danych, które kompilator próbuje umieścić w tym polu. Użyj **/Zm** flagę kompilatora, aby określić większa wartość dla prekompilowanego pliku nagłówkowego. Aby uzyskać więcej informacji, zobacz [/Zm (Określ Limit pamięci Prekompilowanego nagłówka alokacji)](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md).