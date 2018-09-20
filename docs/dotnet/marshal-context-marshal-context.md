---
title: marshal_context::marshal_context | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- msclr::interop::marshal_context::marshal_context
- marshal_context::marshal_context
- msclr.interop.marshal_context.marshal_context
- marshal_context.marshal_context
dev_langs:
- C++
helpviewer_keywords:
- marshal_context class [C++], operations
ms.assetid: 5f08c895-60b0-4f72-97ff-7ae37c68e853
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 02f238a8d9b9d484073794b9a75888325d95107b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399447"
---
# <a name="marshalcontextmarshalcontext"></a>marshal_context::marshal_context

Konstruuje `marshal_context` obiekt ma być używany do konwersji danych między typami danych zarządzanego i natywnego.

## <a name="syntax"></a>Składnia

```
marshal_context();
```

## <a name="remarks"></a>Uwagi

Konwersje niektórych danych wymaga kontekstu marshal. Zobacz [Overview of Marshaling w C++](../dotnet/overview-of-marshaling-in-cpp.md) Aby uzyskać więcej informacji na temat tłumaczenia, które wymagają kontekstu i organizowania plik, który musi być ujęta w aplikacji.

## <a name="example"></a>Przykład

Zobacz przykład [marshal_context::marshal_as](../dotnet/marshal-context-marshal-as.md).

## <a name="requirements"></a>Wymagania

**Plik nagłówka:** \<msclr\marshal.h >, \<msclr\marshal_windows.h >, \<msclr\marshal_cppstd.h >, lub \<msclr\marshal_atl.h >

**Namespace:** msclr::interop

## <a name="see-also"></a>Zobacz też

[Omówienie marshalingu w języku C++](../dotnet/overview-of-marshaling-in-cpp.md)<br/>
[marshal_as](../dotnet/marshal-as.md)<br/>
[marshal_context, klasa](../dotnet/marshal-context-class.md)