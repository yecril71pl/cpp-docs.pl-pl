---
title: Klasa Icommandtarget
ms.date: 11/04/2016
f1_keywords:
- ICommandTarget
- AFXWINFORMS/ICommandTarget
- AFXWINFORMS/ICommandTarget::Initialize
helpviewer_keywords:
- ICommandTarget interface [MFC]
ms.assetid: dd9927f6-3479-4e7c-8ef9-13206cf901f3
ms.openlocfilehash: a224b868ea1923bb4f84b0d682c71fadb63da572
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57299944"
---
# <a name="icommandtarget-interface"></a>Klasa Icommandtarget

Udostępnia kontrolkę użytkownika z interfejsem w celu odbierania poleceń od obiektu źródła polecenia.

## <a name="syntax"></a>Składnia

```
interface class ICommandTarget
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[ICommandTarget::Initialize](#initialize)|Inicjuje obiekt docelowy polecenia.|

## <a name="remarks"></a>Uwagi

Hostowanie kontrolki użytkownika w widoku MFC [CWinFormsView](../../mfc/reference/cwinformsview-class.md) polecenia tras i aktualizacja poleceń interfejsu użytkownika wiadomości do formantu użytkownika, aby zezwalała na obsługę jego poleceń MFC (na przykład ramek elementów menu i przycisków paska narzędzi). Implementując `ICommandTarget`, podać odwołanie do formantu użytkownika [ICommandSource](../../mfc/reference/icommandsource-interface.md) obiektu.

Zobacz [jak: Dodawanie routingu poleceń do formantu programu Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) przykład sposobu użycia `ICommandTarget`.

Aby uzyskać więcej informacji na temat korzystania z Windows Forms, zobacz [za pomocą kontrolki użytkownika formularza Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwinforms.h (zdefiniowany w zestawie atlmfc\lib\mfcmifc80.dll)

##  <a name="initialize"></a> ICommandTarget::Initialize

Inicjuje obiekt docelowy polecenia.

```
void Initialize(ICommandSource^ cmdSource);
```

### <a name="parameters"></a>Parametry

*cmdSource*<br/>
Dojście do obiektu źródła polecenia.

### <a name="remarks"></a>Uwagi

Hostowanie kontrolki użytkownika w widoku MFC CWinFormsView kieruje polecenia i komunikaty interfejs użytkownika polecenia aktualizacji do formantu użytkownika, aby zezwolić na obsługę jego poleceń MFC.

Ta metoda inicjuje obiekt docelowy polecenia i kojarzy ją z cmdSource obiektu źródłowego określonego polecenia. Powinien zostać wywołany w implementacji klasy formantu użytkownika. Podczas inicjowania należy zarejestrować programy obsługi poleceń, za pomocą obiektu źródła polecenia przez ICommandSource::AddCommandHandler wywołujący w implementacji inicjowania. Zobacz jak: Dodawanie routingu poleceń do kontrolki formularzy Windows przykład jak to zrobić za pomocą inicjowania.

## <a name="see-also"></a>Zobacz także

[Instrukcje: dodawanie routingu poleceń do formantu interfejsu Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[Klasa ICommandSource](../../mfc/reference/icommandsource-interface.md)
