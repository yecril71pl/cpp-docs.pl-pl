---
title: Ostrzeżenie RC4005 kompilatora zasobów
ms.date: 11/04/2016
f1_keywords:
- RC4005
helpviewer_keywords:
- RC4005
ms.assetid: 71f03b4a-c9a9-415d-920f-bf2e58507f93
ms.openlocfilehash: 571c4ac285e9477b017dbc21cf9ff733539759d2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613606"
---
# <a name="resource-compiler-warning-rc4005"></a>Ostrzeżenie RC4005 kompilatora zasobów

'Identyfikator': ponowna definicja makra

Identyfikator zdefiniowano dwa razy. Kompilator używał drugi definicji makra.

To ostrzeżenie może być spowodowany przez zdefiniowanie makra w wierszu polecenia i w kodzie adresem `#define` dyrektywy. On również może być spowodowane makra zaimportowane z plików dołączanych.

Aby usunąć to ostrzeżenie, usuń jedną z definicji lub użyj `#undef` dyrektywy przed definicją drugiego.