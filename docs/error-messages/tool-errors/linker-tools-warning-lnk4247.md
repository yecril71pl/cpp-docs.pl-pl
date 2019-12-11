---
title: Ostrzeżenie LNK4247 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4247
helpviewer_keywords:
- LNK4247
ms.assetid: 085d7fdf-9eaf-4641-8473-6eaadd073c7b
ms.openlocfilehash: 344c219fa1f3daa1e5f9c31431e608f5e7036400
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991153"
---
# <a name="linker-tools-warning-lnk4247"></a>Ostrzeżenie LNK4247 narzędzi konsolidatora

punkt wejścia "decorated_function_name" ma już atrybut wątku; Zignorowano element "Attribute"

Punkt wejścia określony za pomocą elementu [/entry (symbol punktu wejścia)](../../build/reference/entry-entry-point-symbol.md)ma atrybut Threading, ale określono również [/CLRTHREADATTRIBUTE (ustaw atrybut wątku CLR)](../../build/reference/clrthreadattribute-set-clr-thread-attribute.md) z innym modelem wątkowości.

Konsolidator zignorował wartość określoną za pomocą/CLRTHREADATTRIBUTE.

Aby usunąć to ostrzeżenie:

- Usuń/CLRTHREADATTRIBUTE z kompilacji.

- Usuń atrybut z pliku kodu źródłowego.

- Usuń atrybut ze źródła i/CLRTHREADATTRIBUTE z kompilacji i Zaakceptuj domyślny model wątkowości CLR.

- Zmień wartość przekazaną do/CLRTHREADATTRIBUTE, tak aby była ona zgodna z atrybutem w źródle.

- Zmień atrybut w elemencie source, tak aby zgadzał się z wartością przekazaną do/CLRTHREADATTRIBUTE.

Poniższy przykład generuje LNK4247 narzędzi KONSOLIDATORA

```cpp
// LNK4247.cpp
// compile with: /clr /c
// post-build command: link /CLRTHREADATTRIBUTE:STA LNK4247.obj /entry:functionTitle /SUBSYSTEM:Console
[System::MTAThreadAttribute]
void functionTitle (){}
```
