---
title: Ostrzeżenie RC4005 kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC4005
dev_langs:
- C++
helpviewer_keywords:
- RC4005
ms.assetid: 71f03b4a-c9a9-415d-920f-bf2e58507f93
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 589fd008b3927887a8144b2fc63d2cbbde2af913
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028522"
---
# <a name="resource-compiler-warning-rc4005"></a>Ostrzeżenie RC4005 kompilatora zasobów

'Identyfikator': ponowna definicja makra

Identyfikator zdefiniowano dwa razy. Kompilator używał drugi definicji makra.

To ostrzeżenie może być spowodowany przez zdefiniowanie makra w wierszu polecenia i w kodzie adresem `#define` dyrektywy. On również może być spowodowane makra zaimportowane z plików dołączanych.

Aby usunąć to ostrzeżenie, usuń jedną z definicji lub użyj `#undef` dyrektywy przed definicją drugiego.