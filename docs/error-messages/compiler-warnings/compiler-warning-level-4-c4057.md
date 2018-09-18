---
title: Kompilator ostrzeżenie (poziom 4) C4057 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4057
dev_langs:
- C++
helpviewer_keywords:
- C4057
ms.assetid: e75d0645-84c9-4bef-a812-942ed9879aa3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b10ce6b67fd24b4b8db01177af0225deab9dba4b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088010"
---
# <a name="compiler-warning-level-4-c4057"></a>Kompilator ostrzeżenie (poziom 4) C4057

'operator': operator pośredni "identifier1" do nieco innych typów podstawowych z "identifier2"

Dwa wyrażenia wskaźnika odwoływać się do innych typów podstawowych. Wyrażenia są używane bez konwersji.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny

1. Mieszanie typów ze znakiem i bez znaku.

1. Mieszanie **krótki** i **długie** typów.