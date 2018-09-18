---
title: Wyliczenie ATL_URL_SCHEME | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ATLUTIL/ATL::ATL_URL_SCHEME
ms.assetid: f4131046-8ba0-4ec1-8209-84203f05d20e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d2883232d673bd52a9afff0cd5e76ea29ceb4120
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074412"
---
# <a name="atlurlscheme"></a>ATL_URL_SCHEME

Członkowie to wyliczenie zapewnia stałe dla schematów zrozumiałe [CUrl](curl-class.md).

## <a name="syntax"></a>Składnia

```
enum ATL_URL_SCHEME{
   ATL_URL_SCHEME_UNKNOWN = -1,
   ATL_URL_SCHEME_FTP     = 0,
   ATL_URL_SCHEME_GOPHER  = 1,
   ATL_URL_SCHEME_HTTP    = 2,
   ATL_URL_SCHEME_HTTPS   = 3,
   ATL_URL_SCHEME_FILE    = 4,
   ATL_URL_SCHEME_NEWS    = 5,
   ATL_URL_SCHEME_MAILTO  = 6,
   ATL_URL_SCHEME_SOCKS   = 7
};
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlutil.h

## <a name="see-also"></a>Zobacz też

[Pojęcia](../active-template-library-atl-concepts.md)<br/>
[CUrl::SetScheme](curl-class.md#setscheme)<br/>
[CUrl::GetScheme](curl-class.md#getscheme)
