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
ms.openlocfilehash: d91221dd509122ebbd6490c2de7fab1ce51eb2f8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210733"
---
# <a name="icommandtextimpl-class"></a>ICommandTextImpl — Klasa

Dostarcza implementację interfejsu [ICommandText](/previous-versions/windows/desktop/ms714914(v=vs.85)) .

## <a name="syntax"></a>Składnia

```cpp
template <class T >
class ATL_NO_VTABLE ICommandTextImpl
   : public ICommandImpl<T, ICommandText>
```

### <a name="parameters"></a>Parametry

*&*<br/>
Klasa polecenia pochodna od `ICommandTextImpl`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** altdb. h

## <a name="members"></a>Members

### <a name="interface-methods"></a>Metody interfejsu

|||
|-|-|
|[GetCommandText](#getcommandtext)|Zwraca polecenie tekstowe ustawione przez ostatnie wywołanie metody [SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md).|
|[SetCommandText](#setcommandtext)|Ustawia tekst polecenia, zastępując istniejący tekst polecenia.|

### <a name="data-members"></a>Elementy członkowskie danych

|||
|-|-|
|[m_strCommandText](#strcommandtext)|Przechowuje tekst polecenia.|

## <a name="remarks"></a>Uwagi

Obowiązkowy interfejs dla poleceń.

## <a name="icommandtextimplgetcommandtext"></a><a name="getcommandtext"></a>ICommandTextImpl:: GetCommandText

Zwraca polecenie tekstowe ustawione przez ostatnie wywołanie metody [SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md).

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(GetCommandText)(GUID * pguidDialect,
   LPOLESTR * ppwszCommand);
```

#### <a name="parameters"></a>Parametry

Zobacz [ICommandText:: GetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) w *dokumentacji programisty OLE DB*. Parametr *pguidDialect* jest domyślnie ignorowany.

## <a name="icommandtextimplsetcommandtext"></a><a name="setcommandtext"></a>ICommandTextImpl:: SetCommandText

Ustawia tekst polecenia, zastępując istniejący tekst polecenia.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(SetCommandText)(REFGUID rguidDialect,
   LPCOLESTR pwszCommand);
```

#### <a name="parameters"></a>Parametry

Zobacz [ICommandText:: SetCommandText](/previous-versions/windows/desktop/ms709757(v=vs.85)) w *dokumentacji programisty OLE DB*.

## <a name="icommandtextimplm_strcommandtext"></a><a name="strcommandtext"></a>ICommandTextImpl:: m_strCommandText

Zapisuje ciąg tekstowy polecenia.

### <a name="syntax"></a>Składnia

```cpp
CComBSTR m_strCommandText;
```

## <a name="see-also"></a>Zobacz też

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
