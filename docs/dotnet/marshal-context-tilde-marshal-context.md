---
title: marshal_context::~marshal_context
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- marshal_context::~marshal_context
- msclr.interop.marshal_context.~marshal_context
- marshal_context.~marshal_context
- msclr::interop::marshal_context::~marshal_context
- ~marshal_context
helpviewer_keywords:
- marshal_context class [C++], operations
ms.assetid: 34c41b38-4c33-4f61-b74e-831ac46b4ab5
ms.openlocfilehash: 3bf16ab2dde4047fb845cd700821d097f733a4d2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528222"
---
# <a name="marshalcontextmarshalcontext"></a>marshal_context::~marshal_context

Niszczy `marshal_context` obiektu.

## <a name="syntax"></a>Składnia

```
~marshal_context();
```

## <a name="remarks"></a>Uwagi

Konwersje niektórych danych wymaga kontekstu marshal. Zobacz [Overview of Marshaling w C++](../dotnet/overview-of-marshaling-in-cpp.md) Aby uzyskać więcej informacji na temat tłumaczenia, które wymagają kontekstu i organizowania plik, który musi być ujęta w aplikacji.

Usuwanie `marshal_context` obiektu spowoduje unieważnienie danych przekonwertowane przez ten kontekst. Jeśli chcesz zachować dane po `marshal_context` obiekt jest niszczony, należy ręcznie skopiować dane do zmiennej, który będzie aktualny.

## <a name="requirements"></a>Wymagania

**Plik nagłówka:** \<msclr\marshal.h >, \<msclr\marshal_windows.h >, \<msclr\marshal_cppstd.h >, lub \<msclr\marshal_atl.h >

**Namespace:** msclr::interop

## <a name="see-also"></a>Zobacz też

[Omówienie marshalingu w języku C++](../dotnet/overview-of-marshaling-in-cpp.md)<br/>
[marshal_as](../dotnet/marshal-as.md)<br/>
[marshal_context, klasa](../dotnet/marshal-context-class.md)