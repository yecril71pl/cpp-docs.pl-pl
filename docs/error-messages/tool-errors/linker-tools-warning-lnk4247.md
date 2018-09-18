---
title: Ostrzeżenie LNK4247 narzędzi konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4247
dev_langs:
- C++
helpviewer_keywords:
- LNK4247
ms.assetid: 085d7fdf-9eaf-4641-8473-6eaadd073c7b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2d84a5964cb8df5d2973b6031da55d48dade584e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46078013"
---
# <a name="linker-tools-warning-lnk4247"></a>Ostrzeżenie LNK4247 narzędzi konsolidatora

punkt wejścia "decorated_function_name" ma już atrybut wątku; "attribute" zignorowany

Punkt wejścia określony za pomocą [/Entry (Symbol punktu wejścia)](../../build/reference/entry-entry-point-symbol.md), ma atrybut wątkowości, ale [/CLRTHREADATTRIBUTE (Ustaw wątku atrybut CLR)](../../build/reference/clrthreadattribute-set-clr-thread-attribute.md) również została określona za pomocą innego modelu wątkowości.

Konsolidator ignorowana wartość określony za pomocą /CLRTHREADATTRIBUTE.

Aby rozwiązać tego ostrzeżenia:

- Usuń /CLRTHREADATTRIBUTE z kompilacji.

- Usuń atrybut z pliku kodu źródłowego.

- Usuń zarówno atrybut ze źródła i /CLRTHREADATTRIBUTE z kompilacji, a następnie zaakceptuj domyślny model wątkowości CLR.

- Zmień wartość przekazana do /CLRTHREADATTRIBUTE, w taki sposób, że zgadza się z atrybutem w źródle.

- Taki sposób, że zgadza się z wartością przekazywaną do /CLRTHREADATTRIBUTE, należy zmienić atrybutu w lokalizacji źródłowej.

Poniższy przykład spowoduje wygenerowanie LNK4247

```
// LNK4247.cpp
// compile with: /clr /c
// post-build command: link /CLRTHREADATTRIBUTE:STA LNK4247.obj /entry:functionTitle /SUBSYSTEM:Console
[System::MTAThreadAttribute]
void functionTitle (){}
```