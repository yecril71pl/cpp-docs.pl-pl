---
title: FtmBase::CreateGlobalInterfaceTable, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::CreateGlobalInterfaceTable
dev_langs:
- C++
helpviewer_keywords:
- CreateGlobalInterfaceTable method
ms.assetid: bb82a0c5-22b9-4844-9204-7922033d8b07
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6c042b6bd17da3459f499f9eb1c9167343c2e2ab
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42578776"
---
# <a name="ftmbasecreateglobalinterfacetable-method"></a>FtmBase::CreateGlobalInterfaceTable — Metoda

Tworzy tabelę interfejsu globalnego (GIT).

## <a name="syntax"></a>Składnia

```cpp
static HRESULT CreateGlobalInterfaceTable(
   __out IGlobalInterfaceTable **git
);
```

### <a name="parameters"></a>Parametry

*usługi git*  
Gdy ta operacja zostanie ukończone, wskaźnik tabeli interfejsu globalnego.

## <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz `IGlobalInterfaceTable` tematu w **interfejsów COM** podrzędny z **odwołanie COM** w bibliotece MSDN.

## <a name="requirements"></a>Wymagania

**Nagłówek:** ftm.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[FtmBase, klasa](../windows/ftmbase-class.md)