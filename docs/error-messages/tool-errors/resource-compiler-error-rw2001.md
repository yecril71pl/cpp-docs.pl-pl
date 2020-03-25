---
title: Błąd kompilatora zasobów RW2001
ms.date: 11/04/2016
f1_keywords:
- RW2001
helpviewer_keywords:
- RW2001
ms.assetid: 963bdc7d-6ebe-4378-8bbc-47dfcf5d330c
ms.openlocfilehash: 900bfed9d57af0f6f5dd8fac19380bb7c382addc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190745"
---
# <a name="resource-compiler-error-rw2001"></a>Błąd kompilatora zasobów RW2001

Nieprawidłowa dyrektywa w wstępnie przetworzonym pliku RC

Plik RC zawiera dyrektywę **#pragma** .

Użyj dyrektywy preprocesora **#ifndef** ze stałą **RC_INVOKED** , którą kompilator zasobów definiuje podczas przetwarzania pliku dołączanego. Umieść dyrektywę **#pragma** wewnątrz bloku kodu, który nie jest przetwarzany, gdy zostanie zdefiniowana stała **RC_INVOKED** . Kod w bloku jest przetwarzany tylko przez kompilator C/C++ , a nie przez kompilator zasobów. Następujący przykładowy kod demonstruje tę technikę:

```
#ifndef RC_INVOKED
#pragma pack(2)  // C/C++ only, ignored by Resource Compiler
#endif
```

Dyrektywa preprocesora **#pragma** nie ma znaczenia w. Plik RC. Dyrektywa preprocesora **#include** jest często używana w. Plik RC obejmujący plik nagłówka (plik niestandardowego nagłówka bazujący na projekcie lub standardowy plik nagłówkowy dostarczany przez firmę Microsoft z jednym z jego produktów). Niektóre z tych plików dołączanych zawierają dyrektywę **#pragma** . Ponieważ plik nagłówkowy może zawierać jeden lub więcej innych plików nagłówkowych, plik zawierający **nie#pragmaą** dyrektywę może nie być natychmiast oczywisty.

Technikę **RC_INVOKED #ifndef** może kontrolować, w tym pliki nagłówkowe w plikach nagłówkowych opartych na projekcie.
