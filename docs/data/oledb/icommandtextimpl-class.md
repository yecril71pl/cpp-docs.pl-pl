---
title: ICommandTextImpl — Klasa
ms.date: 11/04/2016
f1_keywords:
- ICommandText
- GetCommandText
- ICommandTextImpl.GetCommandText
- ICommandTextImpl::GetCommandText
- ATL::ICommandTextImpl::m_strCommandText
- ICommandTextImpl<T>::m_strCommandText
- m_strCommandText
- ICommandTextImpl.m_strCommandText
- ICommandTextImpl::m_strCommandText
- ATL::ICommandTextImpl<T>::m_strCommandText
- ATL.ICommandTextImpl.m_strCommandText
- ICommandTextImpl.SetCommandText
- ICommandTextImpl::SetCommandText
- SetCommandText
helpviewer_keywords:
- ICommandText class
- GetCommandText method
- m_strCommandText
- SetCommandText method
ms.assetid: 9c2715cc-1e55-4468-8327-85341617ed46
ms.openlocfilehash: fafd1198776c558ff39ef35c0b7beca538e976ae
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677698"
---
# <a name="icommandtextimpl-class"></a>ICommandTextImpl — Klasa

Udostępnia implementację na potrzeby [ICommandText](/previous-versions/windows/desktop/ms714914) interfejsu.

## <a name="syntax"></a>Składnia

```cpp
template <class T >
class ATL_NO_VTABLE ICommandTextImpl
   : public ICommandImpl<T, ICommandText>
```

### <a name="parameters"></a>Parametry

*T*<br/>
Klasa polecenia pochodną `ICommandTextImpl`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** altdb.h

## <a name="members"></a>Elementy członkowskie

### <a name="interface-methods"></a>Metody interfejsu

|||
|-|-|
|[GetCommandText](#getcommandtext)|Zwraca tekst polecenia ustawione przez ostatnie wywołanie elementu [SetCommandText —](../../data/oledb/icommandtextimpl-setcommandtext.md).|
|[SetCommandText](#setcommandtext)|Ustawia tekst polecenia, zastępując istniejący tekst polecenia.|

### <a name="data-members"></a>Elementy członkowskie danych

|||
|-|-|
|[m_strCommandText](#strcommandtext)|Przechowuje tekst polecenia.|

## <a name="remarks"></a>Uwagi

Obowiązkowego interfejsu na polecenia.

## <a name="getcommandtext"></a> ICommandTextImpl::GetCommandText

Zwraca tekst polecenia ustawione przez ostatnie wywołanie elementu [SetCommandText —](../../data/oledb/icommandtextimpl-setcommandtext.md).

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(GetCommandText)(GUID * pguidDialect, 
   LPOLESTR * ppwszCommand);
```

#### <a name="parameters"></a>Parametry

Zobacz [ICommandText::GetCommandText](/previous-versions/windows/desktop/ms709825) w *OLE DB Podręcznik programisty*. *PguidDialect* parametr jest ignorowany, domyślnie.

## <a name="setcommandtext"></a> ICommandTextImpl::SetCommandText

Ustawia tekst polecenia, zastępując istniejący tekst polecenia.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(SetCommandText)(REFGUID rguidDialect, 
   LPCOLESTR pwszCommand);
```

#### <a name="parameters"></a>Parametry

Zobacz [ICommandText::SetCommandText](/previous-versions/windows/desktop/ms709757) w *OLE DB Podręcznik programisty*.

## <a name="strcommandtext"></a> ICommandTextImpl::m_strCommandText

Zapisuje ciąg tekstu polecenia.

### <a name="syntax"></a>Składnia

```cpp
CComBSTR m_strCommandText;
```

## <a name="see-also"></a>Zobacz też

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)