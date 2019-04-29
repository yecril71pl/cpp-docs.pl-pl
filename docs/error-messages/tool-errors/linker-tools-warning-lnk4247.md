---
title: Ostrzeżenie LNK4247 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4247
helpviewer_keywords:
- LNK4247
ms.assetid: 085d7fdf-9eaf-4641-8473-6eaadd073c7b
ms.openlocfilehash: cd4108f8bd06ec7a0b2d2eb9fab13917174b797b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62346963"
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