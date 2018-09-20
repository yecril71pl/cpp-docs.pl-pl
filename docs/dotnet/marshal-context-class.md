---
title: marshal_context Class | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- marshal_context
dev_langs:
- C++
helpviewer_keywords:
- marshal_context class [C++]
ms.assetid: 241b0cf6-4ca4-4812-aaee-d671c11dc034
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: fc3399ee088a0430ca857c3e421742ee484d337a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413319"
---
# <a name="marshalcontext-class"></a>marshal_context — Klasa

Ta klasa konwertuje dane między środowiskami macierzystymi i zarządzanymi.

## <a name="syntax"></a>Składnia

```
class marshal_context
```

## <a name="remarks"></a>Uwagi

Użyj `marshal_context` klasy podczas konwersji danych, które wymagają kontekst. Zobacz [Overview of Marshaling w C++](../dotnet/overview-of-marshaling-in-cpp.md) uzyskać więcej informacji o jakie konwersje wymaga kontekstu i organizowania plik, który ma zostać uwzględniony. Organizowanie, korzystając z kontekstu wynik jest prawidłowy tylko do `marshal_context` niszczony jest obiekt. Aby zachować wyników, należy skopiować dane.

Taki sam `marshal_context` może służyć do wielu konwersji danych. Ponowne używanie kontekstu w ten sposób nie wpływa na wyniki z poprzedniego wywołania organizowania.

## <a name="requirements"></a>Wymagania

**Plik nagłówka:** \<msclr\marshal.h >, \<msclr\marshal_windows.h >, \<msclr\marshal_cppstd.h >, lub \<msclr\marshal_atl.h >

**Namespace:** msclr::interop

## <a name="see-also"></a>Zobacz też

[Omówienie marshalingu w języku C++](../dotnet/overview-of-marshaling-in-cpp.md)<br/>
[marshal_as](../dotnet/marshal-as.md)