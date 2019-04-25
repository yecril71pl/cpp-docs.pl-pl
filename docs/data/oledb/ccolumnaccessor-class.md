---
title: CColumnAccessor — Klasa
ms.date: 11/04/2016
f1_keywords:
- CColumnAccessor
- ATL::CColumnAccessor
- ATL.CColumnAccessor
helpviewer_keywords:
- CColumnAccessor class
ms.assetid: 6ce1e67f-6a20-490d-9326-c168b43eee7e
ms.openlocfilehash: 2d65fb047e758f449ed76c954bb4ac0c3623f6dd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209311"
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

## <a name="see-also"></a>Zobacz także

[Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)