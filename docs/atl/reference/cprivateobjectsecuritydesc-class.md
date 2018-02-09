---
title: Klasa CPrivateObjectSecurityDesc | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::ConvertToAutoInherit
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Create
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Get
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Set
dev_langs:
- C++
helpviewer_keywords:
- CPrivateObjectSecurityDesc class
ms.assetid: 2c4bbb13-bf99-4833-912a-197f6815bb5d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e4845d652d2b1dceb8ffc0f2772f88565eb81e29
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="cprivateobjectsecuritydesc-class"></a>Klasa CPrivateObjectSecurityDesc
Ta klasa reprezentuje obiekt deskryptora zabezpieczeń obiektu prywatnego.  
  
## <a name="syntax"></a>Składnia  
  
```
class CPrivateObjectSecurityDesc : public CSecurityDesc
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc](#cprivateobjectsecuritydesc)|Konstruktor.|  
|[CPrivateObjectSecurityDesc::~CPrivateObjectSecurityDesc](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPrivateObjectSecurityDesc::ConvertToAutoInherit](#converttoautoinherit)|Wywołaj tę metodę, aby przekonwertować deskryptora zabezpieczeń i jego listy kontroli dostępu (ACL) do formatu, który obsługuje automatyczne propagacji zapisów dziedziczne kontroli dostępu (ACE).|  
|[CPrivateObjectSecurityDesc::Create](#create)|Wywołanie tej metody można przydzielić i zainicjować deskryptor zabezpieczeń autorelacyjnym prywatnego obiektu utworzonego przez wywołanie Menedżera zasobów.|  
|[CPrivateObjectSecurityDesc::Get](#get)|Wywołaj tę metodę w celu pobrania informacji z deskryptora zabezpieczeń obiektu prywatnego.|  
|[CPrivateObjectSecurityDesc::Set](#set)|Wywołanie tej metody można zmodyfikować deskryptora zabezpieczeń obiektu prywatnego.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[operator =](#operator_eq)|Operator przypisania.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa pochodzi od [CSecurityDesc](../../atl/reference/csecuritydesc-class.md), udostępnia metody do tworzenia i zarządzania deskryptora zabezpieczeń obiektu prywatnego.  
  
 Aby obejrzeć wprowadzenie do modelu kontroli dostępu w systemie Windows, temacie [kontroli dostępu](http://msdn.microsoft.com/library/windows/desktop/aa374860) w zestawie Windows SDK.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CSecurityDesc](../../atl/reference/csecuritydesc-class.md)  
  
 `CPrivateObjectSecurityDesc`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsecurity.h  
  
##  <a name="converttoautoinherit"></a>CPrivateObjectSecurityDesc::ConvertToAutoInherit  
 Wywołaj tę metodę, aby przekonwertować deskryptora zabezpieczeń i jego listy kontroli dostępu (ACL) do formatu, który obsługuje automatyczne propagacji zapisów dziedziczne kontroli dostępu (ACE).  
  
```
bool ConvertToAutoInherit(  
    const CSecurityDesc* pParent,
    GUID* ObjectType,
    bool bIsDirectoryObject,
    PGENERIC_MAPPING GenericMapping) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pParent`  
 Wskaźnik do [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) obiekt odwołuje się do kontenera nadrzędnego obiektu. Jeśli nie ma żadnych kontenera nadrzędnego, ten parametr ma wartość NULL.  
  
 `ObjectType`  
 Wskaźnik do **GUID** strukturę, która określa typ obiektu skojarzone z bieżącym obiektem. Ustaw `ObjectType` na wartość NULL, jeśli obiekt nie ma identyfikatora GUID.  
  
 `bIsDirectoryObject`  
 Określa, czy nowy obiekt może zawierać inne obiekty. Wartość true wskazuje, że nowy obiekt jest kontenerem. Wartość false wskazuje, że nowy obiekt nie jest kontenerem.  
  
 `GenericMapping`  
 Wskaźnik do [GENERIC_MAPPING](http://msdn.microsoft.com/library/windows/desktop/aa446633) strukturę, która określa mapowania z każdego ogólnego prawa do określonych praw dla obiekt.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Tej metody spróbuje określić, czy wpisy kontroli dostępu w DACL kontroli dostępu lista (DACL) i system listy kontroli dostępu (SACL) bieżącego deskryptora zabezpieczeń były dziedziczone z nadrzędnego deskryptora zabezpieczeń. Wywołuje [ConvertToAutoInheritPrivateObjectSecurity](http://msdn.microsoft.com/library/windows/desktop/aa376403) funkcji.  
  
##  <a name="cprivateobjectsecuritydesc"></a>CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc  
 Konstruktor.  
  
```
CPrivateObjectSecurityDesc() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Inicjuje `CPrivateObjectSecurityDesc` obiektu.  
  
##  <a name="dtor"></a>CPrivateObjectSecurityDesc:: ~ CPrivateObjectSecurityDesc  
 Destruktor.  
  
```
~CPrivateObjectSecurityDesc() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Destruktor zwalnia wszystkie przydzielone zasoby i usuwa deskryptora zabezpieczeń obiektu prywatnego.  
  
##  <a name="create"></a>CPrivateObjectSecurityDesc::Create  
 Wywołanie tej metody można przydzielić i zainicjować deskryptor zabezpieczeń autorelacyjnym prywatnego obiektu utworzonego przez wywołanie Menedżera zasobów.  
  
```
bool Create(  
    const CSecurityDesc* pParent,
    const CSecurityDesc* pCreator,
    bool bIsDirectoryObject,
    const CAccessToken& Token,
    PGENERIC_MAPPING GenericMapping) throw();

bool Create(  
    const CSecurityDesc* pParent,
    const CSecurityDesc* pCreator,
    GUID* ObjectType,
    bool bIsContainerObject,
    ULONG AutoInheritFlags,
    const CAccessToken& Token,
    PGENERIC_MAPPING GenericMapping) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pParent`  
 Wskaźnik do [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) obiekt odwołuje się do katalogu nadrzędnego, w której jest tworzony nowy obiekt. Ustawiana wartość NULL, jeśli nie ma katalogu nadrzędnego.  
  
 `pCreator`  
 Wskaźnik do dostarczonych przez twórcy obiektu deskryptora zabezpieczeń. Jeśli twórcy obiektów nie przejdzie jawnie informacji o zabezpieczeniach dla nowego obiektu, ustaw ten parametr na wartość NULL.  
  
 `bIsDirectoryObject`  
 Określa, czy nowy obiekt może zawierać inne obiekty. Wartość true wskazuje, że nowy obiekt jest kontenerem. Wartość false wskazuje, że nowy obiekt nie jest kontenerem.  
  
 `Token`  
 Odwołanie do [CAccessToken](../../atl/reference/caccesstoken-class.md) obiekt dla procesu klienta w imieniu którego jest tworzony obiekt.  
  
 `GenericMapping`  
 Wskaźnik do [GENERIC_MAPPING](http://msdn.microsoft.com/library/windows/desktop/aa446633) strukturę, która określa mapowania z każdego ogólnego prawa do określonych praw dla obiekt.  
  
 `ObjectType`  
 Wskaźnik do **GUID** strukturę, która określa typ obiektu skojarzone z bieżącym obiektem. Ustaw `ObjectType` na wartość NULL, jeśli obiekt nie ma identyfikatora GUID.  
  
 *bIsContainerObject*  
 Określa, czy nowy obiekt może zawierać inne obiekty. Wartość true wskazuje, że nowy obiekt jest kontenerem. Wartość false wskazuje, że nowy obiekt nie jest kontenerem.  
  
 `AutoInheritFlags`  
 Zestaw flagi bitów, które kontrolują sposób wpisów kontroli dostępu (ACE) są dziedziczone z `pParent`. Zobacz [CreatePrivateObjectSecurityEx](http://msdn.microsoft.com/library/windows/desktop/aa446581) więcej szczegółów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wywołuje [CreatePrivateObjectSercurity](http://msdn.microsoft.com/library/windows/desktop/aa376405) lub [CreatePrivateObjectSecurityEx](http://msdn.microsoft.com/library/windows/desktop/aa446581).  
  
 Druga metoda zezwala na określanie typu obiektu identyfikator GUID nowego obiektu lub kontrolowanie sposobu ACE są dziedziczone.  
  
> [!NOTE]
>  Deskryptor zabezpieczeń autorelacyjnym jest deskryptora zabezpieczeń, która przechowuje wszystkie jej informacje o zabezpieczeniach w ciągłego bloku pamięci.  
  
##  <a name="get"></a>CPrivateObjectSecurityDesc::Get  
 Wywołaj tę metodę w celu pobrania informacji z deskryptora zabezpieczeń obiektu prywatnego.  
  
```
bool Get(  
    SECURITY_INFORMATION si,
    CSecurityDesc* pResult) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `si`  
 Zestaw flag bitowych, które wskazują części można pobrać deskryptora zabezpieczeń. Ta wartość może być kombinacją [SECURITY_INFORMATION](http://msdn.microsoft.com/library/windows/desktop/aa379573) bit flagi.  
  
 `pResult`  
 Wskaźnik do [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) obiekt, który odbiera kopię żądane informacje z Podany deskryptor zabezpieczeń.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Deskryptor zabezpieczeń ma strukturę i skojarzone dane, który zawiera informacje dotyczące zabezpieczeń dla obiektu zabezpieczanego.  
  
##  <a name="operator_eq"></a>CPrivateObjectSecurityDesc::operator =  
 Operator przypisania.  
  
```
CPrivateObjectSecurityDesc& operator= (const CPrivateObjectSecurityDesc& rhs) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rhs`  
 `CPrivateObjectSecurityDesc` Obiektu można przypisać do bieżącego obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca zaktualizowane `CPrivateObjectSecurityDesc` obiektu.  
  
##  <a name="set"></a>CPrivateObjectSecurityDesc::Set  
 Wywołanie tej metody można zmodyfikować deskryptora zabezpieczeń obiektu prywatnego.  
  
```
bool Set(  
    SECURITY_INFORMATION si,
    const CSecurityDesc& Modification,
    PGENERIC_MAPPING GenericMapping,
    const CAccessToken& Token) throw();

bool Set(  
    SECURITY_INFORMATION si,
    const CSecurityDesc& Modification,
    ULONG AutoInheritFlags,
    PGENERIC_MAPPING GenericMapping,
    const CAccessToken& Token) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `si`  
 Zestaw flagi bitów, które wskazują części można ustawić deskryptora zabezpieczeń. Ta wartość może być kombinacją [SECURITY_INFORMATION](http://msdn.microsoft.com/library/windows/desktop/aa379573) bit flagi.  
  
 *Modyfikowanie*  
 Wskaźnik do [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) obiektu. Części deskryptora zabezpieczeń wskazanych przez `si` parametru są stosowane do deskryptora zabezpieczeń obiektu.  
  
 `GenericMapping`  
 Wskaźnik do [GENERIC_MAPPING](http://msdn.microsoft.com/library/windows/desktop/aa446633) strukturę, która określa mapowania z każdego ogólnego prawa do określonych praw dla obiekt.  
  
 `Token`  
 Odwołanie do [CAccessToken](../../atl/reference/caccesstoken-class.md) obiekt dla procesu klienta w imieniu którego jest tworzony obiekt.  
  
 `AutoInheritFlags`  
 Zestaw flagi bitów, które kontrolują sposób wpisów kontroli dostępu (ACE) są dziedziczone z `pParent`. Zobacz [CreatePrivateObjectSecurityEx](http://msdn.microsoft.com/library/windows/desktop/aa446581) więcej szczegółów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Druga metoda zezwala na określanie typu obiektu identyfikator GUID obiektu lub kontrolowanie sposobu ACE są dziedziczone.  
  
## <a name="see-also"></a>Zobacz też  
 [SECURITY_DESCRIPTOR](http://msdn.microsoft.com/library/windows/desktop/aa379561)   
 [Przegląd klas](../../atl/atl-class-overview.md)   
 [Globalne funkcje zabezpieczeń](../../atl/reference/security-global-functions.md)   
 [Klasa CSecurityDesc](../../atl/reference/csecuritydesc-class.md)
