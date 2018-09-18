---
title: Błąd krytyczny C1211 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1211
dev_langs:
- C++
helpviewer_keywords:
- C1211
ms.assetid: df0ca70d-ec6e-4400-926a-b877e2599978
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 444d2bc25c2eddd5ea9a0170272bd3e71b61f94f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018532"
---
# <a name="fatal-error-c1211"></a>Błąd krytyczny C1211

Atrybut niestandardowy TypeForwardedTo nie jest obsługiwany przez wersję zainstalowanego środowiska uruchomieniowego

C1211 występuje, gdy masz kompilatora dla bieżącej wersji, ale środowisko uruchomieniowe języka wspólnego z poprzedniej wersji.

Niektóre funkcje kompilatora może nie działać w poprzedniej wersji w czasie wykonywania.

Aby rozwiązać C1211 instalacji środowiska uruchomieniowego języka wspólnego dostarczanej przez kompilator używasz.

Aby uzyskać więcej informacji, zobacz [przekazywania dalej typów (C + +/ CLI)](../../windows/type-forwarding-cpp-cli.md).