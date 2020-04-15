---
title: Klasa ICommandTarget
ms.date: 11/04/2016
f1_keywords:
- ICommandTarget
- AFXWINFORMS/ICommandTarget
- AFXWINFORMS/ICommandTarget::Initialize
helpviewer_keywords:
- ICommandTarget interface [MFC]
ms.assetid: dd9927f6-3479-4e7c-8ef9-13206cf901f3
ms.openlocfilehash: 865a8a27d96f84f536e40ec5a7bbbbdd9837dfcd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356916"
---
# <a name="icommandtarget-interface"></a>Klasa ICommandTarget

Zapewnia formant użytkownika z interfejsem do odbierania poleceń z obiektu źródłowego polecenia.

## <a name="syntax"></a>Składnia

```
interface class ICommandTarget
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[ICommandTarget::Inicjalizuj](#initialize)|Inicjuje obiekt docelowy polecenia.|

## <a name="remarks"></a>Uwagi

Podczas hostowania formantu użytkownika w widoku MFC, [CWinFormsView](../../mfc/reference/cwinformsview-class.md) trasy poleceń i zaktualizować polecenia komunikaty interfejsu użytkownika do formantu użytkownika, aby umożliwić mu obsługę poleceń MFC (na przykład elementy menu ramki i przyciski paska narzędzi). Implementując `ICommandTarget`, nadać kontroli użytkownika odwołanie do [ICommandSource](../../mfc/reference/icommandsource-interface.md) obiektu.

Zobacz [Jak: Dodawanie routingu poleceń do formantu formularzy systemu Windows,](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) aby uzyskać przykład użycia `ICommandTarget`programu .

Aby uzyskać więcej informacji na temat korzystania z formularzy systemu Windows, zobacz [Korzystanie z formantu użytkownika formularza systemu Windows w programie MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwinforms.h (zdefiniowany w zestawie atlmfc\lib\mfcmifc80.dll)

## <a name="icommandtargetinitialize"></a><a name="initialize"></a>ICommandTarget::Inicjalizuj

Inicjuje obiekt docelowy polecenia.

```
void Initialize(ICommandSource^ cmdSource);
```

### <a name="parameters"></a>Parametry

*źródło cmdSource*<br/>
Dojście do obiektu źródłowego polecenia.

### <a name="remarks"></a>Uwagi

Podczas hostowanie formantu użytkownika w widoku MFC, CWinFormsView trasy poleceń i zaktualizować polecenia komunikaty interfejsu użytkownika do formantu użytkownika, aby umożliwić obsługę poleceń MFC.

Ta metoda inicjuje obiekt docelowy polecenia i kojarzy go z określonym obiektem źródłowym polecenia cmdSource. Należy wywołać w implementacji klasy kontroli użytkownika. Podczas inicjowania należy zarejestrować programy obsługi poleceń z obiektem źródłowym polecenia, wywołując ICommandSource::AddCommandHandler w implementacji Initialize. Zobacz Jak: Dodawanie routingu poleceń do formantu formularzy systemu Windows, aby uzyskać przykład użycia inicjowania w tym celu.

## <a name="see-also"></a>Zobacz też

[Instrukcje: dodawanie routingu poleceń do formantu interfejsu Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[Klasa ICommandSource](../../mfc/reference/icommandsource-interface.md)
