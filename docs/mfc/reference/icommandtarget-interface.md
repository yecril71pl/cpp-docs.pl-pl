---
title: Interfejs obiektu ICommandTarget | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- ICommandTarget
- AFXWINFORMS/ICommandTarget
- AFXWINFORMS/ICommandTarget::Initialize
dev_langs:
- C++
helpviewer_keywords:
- ICommandTarget interface [MFC]
ms.assetid: dd9927f6-3479-4e7c-8ef9-13206cf901f3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b32112fbad516b2550da0cc48cb6c287583d396c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33375580"
---
# <a name="icommandtarget-interface"></a>Interfejs obiektu ICommandTarget
Udostępnia kontrolkę użytkownika przy użyciu interfejsu do odbierania poleceń z obiektem źródłowym polecenia.  
  
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
 Kiedy host kontrolkę użytkownika w widoku MFC [CWinFormsView](../../mfc/reference/cwinformsview-class.md) polecenia tras i aktualizacji polecenia interfejsu użytkownika wiadomości do kontrolki użytkownika, aby umożliwić jego poleceń MFC (na przykład elementów menu ramki i przycisków paska narzędzi). Zaimplementowanie `ICommandTarget`, nadaj odwołanie do kontrolki użytkownika [ICommandSource](../../mfc/reference/icommandsource-interface.md) obiektu.  
  
 Zobacz [porady: dodawanie do formantu formularzy systemu Windows Routing poleceń](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) przykład sposobu użycia `ICommandTarget`.  
  
 Aby uzyskać więcej informacji na temat używania formularzy systemu Windows, zobacz [za pomocą formantu użytkownika formularza systemu Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwinforms.h (zdefiniowany w zestawie atlmfc\lib\mfcmifc80.dll)  
  
##  <a name="initialize"></a> ICommandTarget::Initialize  
 Inicjuje obiekt docelowy polecenia.  
  
```  
void Initialize(ICommandSource^ cmdSource);  
```  
  
### <a name="parameters"></a>Parametry  
 `cmdSource`  
 Dojście do obiektu źródłowego polecenia.  
  
### <a name="remarks"></a>Uwagi  
 Kiedy host kontrolkę użytkownika w widoku MFC, CWinFormsView kieruje poleceń i polecenia interfejsu użytkownika wiadomości do kontrolki użytkownika, aby umożliwić jego poleceń MFC.  
  
 Ta metoda inicjuje obiekt docelowy polecenia i kojarzy ją z cmdSource obiektu źródłowego określonego polecenia. Powinna być wywoływana w implementacji klasy formantu użytkownika. Podczas inicjowania należy zarejestrować programy obsługi poleceń z obiektem źródłowym polecenia przez wywołującego ICommandSource::AddCommandHandler w celu wykonania inicjowania. Zobacz porady: Dodawanie Routing poleceń do formantu formularzy systemu Windows, na przykład dotyczące używania inicjowania w tym celu.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Dodawanie polecenia routingu do systemu Windows formantu formularzy](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)   
 [Klasa ICommandSource](../../mfc/reference/icommandsource-interface.md)



