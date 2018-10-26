---
title: Ccolumnaccessor — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CColumnAccessor
- ATL::CColumnAccessor
- ATL.CColumnAccessor
dev_langs:
- C++
helpviewer_keywords:
- CColumnAccessor class
ms.assetid: 6ce1e67f-6a20-490d-9326-c168b43eee7e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1e55d4c15ca5d5a3733c44cf89b788b85c905513
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50074673"
---
# <a name="ccolumnaccessor-class"></a>CColumnAccessor — Klasa

Generuje kod wprowadzonego konsumenta.

## <a name="syntax"></a>Składnia

```cpp
class CColumnAccessor : public CAccessorBase
```

## <a name="remarks"></a>Uwagi

W wprowadzonego kodu każda kolumna jest powiązany jako osobne metody dostępu. Należy pamiętać, że ta klasa jest używana w wprowadzonego kodu (na przykład, można napotkać go podczas debugowania), ale zwykle nie trzeba używać jej lub jego metod bezpośrednio.

`CColumnAccessor` implementuje następujących metod klasy zastępczej, z których każdy odpowiadają w działaniu innych metod klasy dostępu:

- `CColumnAccessor` Konstruktor; Tworzy i inicjuje `CColumnAccessor` obiektu.

- `CreateAccessor` Przydziela pamięć dla kolumny struktury powiązania i inicjuje elementy członkowskie danych kolumny.

- `BindColumns` Tworzy powiązanie kolumn z metod dostępu.

- `SetParameterBuffer` Przydziela buforów dla parametrów.

- `AddParameter` Dodaje wpis parametr do parametru struktury wpisu.

- `HasOutputColumns` Określa, czy akcesor ma produkt wyjściowy kolumn

- `HasParameters` Określa, czy akcesor ma następujące parametry.

- `BindParameters` Wiąże parametry utworzonych kolumn.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldbcli.h

## <a name="see-also"></a>Zobacz też

[Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)