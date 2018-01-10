# [Programowanie OLE DB](ole-db-programming.md)
## [Omówienie programowania OLE DB](ole-db-programming-overview.md)
### [Konsumenci i dostawcy OLE DB](ole-db-consumers-and-providers.md)
### [Model obiektów OLE DB](ole-db-object-model.md)
### [Szablony i atrybuty OLE DB oraz inne implementacje](ole-db-templates-attributes-and-other-implementations.md)
### [Kwestie projektowania architektonicznego OLE DB](ole-db-architectural-design-issues.md)
## [Szablony konsumentów OLE DB [C++]](ole-db-consumer-templates-cpp.md)
### [Źródła i sesje danych](data-sources-and-sessions.md)
### [Metody dostępu i zestawy wierszy](accessors-and-rowsets.md)
### [Polecenia i tabele](commands-and-tables.md)
### [Rekordy użytkowników](user-records.md)
### [Zestawy wierszy schematu](schema-rowsets.md)
### [Tworzenie konsumenta OLE DB](creating-an-ole-db-consumer.md)
#### [Tworzenie konsumenta OLE DB przy użyciu kreatora](creating-an-ole-db-consumer-using-a-wizard.md)
##### [Tworzenie prostego konsumenta](creating-a-simple-consumer.md)
##### [Implementowanie prostego konsumenta](implementing-a-simple-consumer.md)
##### [Klasy konsumentów generowane przez kreatora](consumer-wizard-generated-classes.md)
##### [Metody konsumenta generowane przez kreatora](consumer-wizard-generated-methods.md)
#### [Tworzenie konsumenta bez użycia kreatora](creating-a-consumer-without-using-a-wizard.md)
### [Praca z szablonami konsumentów OLE DB](working-with-ole-db-consumer-templates.md)
#### [Upraszczanie dostępu do danych za pomocą atrybutów bazy danych](simplifying-data-access-with-database-attributes.md)
#### [Składowe danych dotyczące stanu pola w metodach dostępu generowanych przez kreatora](field-status-data-members-in-wizard-generated-accessors.md)
#### [Przechodzenie przez prosty zestaw wierszy](traversing-a-simple-rowset.md)
#### [Uruchamianie zapytania parametrycznego](issuing-a-parameterized-query.md)
#### [Pobieranie danych](fetching-data.md)
#### [Aktualizowanie zestawów wierszy](updating-rowsets.md)
#### [Korzystanie z procedur składowanych](using-stored-procedures.md)
##### [Definiowanie procedur składowanych](defining-stored-procedures.md)
##### [Parametry wyjściowe](output-parameters.md)
##### [Używanie wielu zestawów wyników z jednej procedury składowanej](using-multiple-result-sets-from-one-stored-procedure.md)
#### [Korzystanie z metod dostępu](using-accessors.md)
##### [Ustalanie, jakiego typu metody dostępu użyć](determining-which-type-of-accessor-to-use.md)
##### [Używanie wielu metod dostępu w zestawie wierszy](using-multiple-accessors-on-a-rowset.md)
##### [Używanie dynamicznych metod dostępu](using-dynamic-accessors.md)
##### [Zastępowanie dynamicznej metody dostępu](overriding-a-dynamic-accessor.md)
##### [Korzystanie z ręcznych metod dostępu](using-manual-accessors.md)
##### [Uzyskiwanie dostępu do danych XML](accessing-xml-data.md)
#### [Uzyskiwanie metadanych za pomocą zestawów wierszy schematu](obtaining-metadata-with-schema-rowsets.md)
#### [Obsługa transakcji w OLE DB](supporting-transactions-in-ole-db.md)
#### [Korzystanie z widoków rekordów OLE DB](using-ole-db-record-views.md)
#### [Korzystanie z istniejącego zestawu rekordów ADO](using-an-existing-ado-recordset.md)
#### [Aktualizowanie kolumny, gdy inna tabela zawiera odwołanie do wiersza](updating-a-column-when-another-table-contains-a-reference-to-the-row.md)
#### [Korzystanie z zakładek](using-bookmarks.md)
#### [Pobieranie obiektu BLOB](retrieving-a-blob.md)
#### [Odbieranie powiadomień](receiving-notifications.md)
## [Szablony dostawców OLE DB (C++)](ole-db-provider-templates-cpp.md)
### [Architektura szablonu dostawcy OLE DB](ole-db-provider-template-architecture.md)
#### [Interfejsy obiektu źródła danych](data-source-object-interfaces.md)
#### [Interfejsy obiektu sesji](session-object-interfaces.md)
#### [Interfejsy obiektu zestawu wierszy](rowset-object-interfaces.md)
#### [Interfejsy obiektu polecenia](command-object-interfaces.md)
#### [Interfejsy obiektu transakcji](transaction-object-interfaces.md)
#### [Mapy właściwości](property-maps.md)
#### [Rekord użytkownika](user-record.md)
### [Tworzenie dostawcy OLE DB](creating-an-ole-db-provider.md)
#### [Tworzenie projektu dla dostawcy](creating-a-project-for-the-provider.md)
#### [Tworzenie dostawcy](creating-the-provider.md)
#### [Pliki dostawcy generowane przez kreatora](provider-wizard-generated-files.md)
##### [CMyProviderSource (MyProviderDS.H)](cmyprovidersource-myproviderds-h.md)
##### [CMyProviderSession (MyProviderSess.H)](cmyprovidersession-myprovidersess-h.md)
##### [CMyProviderCommand (MyProviderRS.H)](cmyprovidercommand-myproviderrs-h.md)
##### [CMyProviderRowset (MyProviderRS.H)](cmyproviderrowset-myproviderrs-h.md)
##### [CMyProviderWindowsFile](cmyproviderwindowsfile.md)
#### [Tworzenie prostego dostawcy tylko do odczytu](creating-a-simple-read-only-provider.md)
##### [Implementowanie prostego dostawcy tylko do odczytu](implementing-the-simple-read-only-provider.md)
###### [Wczytywanie ciągów do dostawcy OLE DB](reading-strings-into-the-ole-db-provider.md)
###### [Przechowywanie ciągów w dostawcy OLE DB](storing-strings-in-the-ole-db-provider.md)
##### [Udoskonalanie prostego dostawcy tylko do odczytu](enhancing-the-simple-read-only-provider.md)
###### [Modyfikowanie dziedziczenia obiektu RMyProviderRowset](modifying-the-inheritance-of-rmyproviderrowset.md)
###### [Dynamicznie określanie kolumn zwracanych do konsumenta](dynamically-determining-columns-returned-to-the-consumer.md)
##### [Testowanie dostawcy tylko do odczytu](testing-the-read-only-provider.md)
#### [Tworzenie aktualizowalnego dostawcy](creating-an-updatable-provider.md)
### [Praca z szablonami dostawców OLE DB](working-with-ole-db-provider-templates.md)
#### [Dodawanie interfejsu do dostawcy](adding-an-interface-to-your-provider.md)
#### [Odwoływanie się do właściwości w dostawcy](referencing-a-property-in-your-provider.md)
#### [Ustawianie właściwości w dostawcy](setting-properties-in-your-provider.md)
#### [Dynamiczne powiązanie kolumn w dostawcy](dynamically-binding-columns-in-your-provider.md)
#### [Obsługa wolnych wątków w dostawcy](supporting-free-threading-in-your-provider.md)
#### [Testowanie dostawcy](testing-your-provider.md)
#### [Debugowanie dostawcy](debugging-your-provider.md)
#### [Konwertowanie danych nieobsługiwanych przez dostawcę](converting-data-not-supported-by-the-provider.md)
### [Zaawansowane techniki dostawcy](advanced-provider-techniques.md)
#### [Obsługa powiadomień](supporting-notifications.md)
#### [Obsługa zestawów wierszy schematu](supporting-schema-rowsets.md)
#### [Obsługa dostawców dla zakładek](provider-support-for-bookmarks.md)
#### [Przechodzenie testów zgodności z OLE DB](passing-ole-db-conformance-tests.md)
#### [Buforowanie zasobów i usługi OLE DB](ole-db-resource-pooling-and-services.md)
##### [Buforowanie zasobów w aplikacji OLE DB](resource-pooling-in-your-ole-db-application.md)
##### [Włączanie i wyłączanie usług OLE DB](enabling-and-disabling-ole-db-services.md)
###### [Włączanie i wyłączanie usług dla dostawcy](enabling-and-disabling-services-for-a-provider.md)
###### [Zastępowanie ustawień domyślnych usługi dostawcy](overriding-provider-service-defaults.md)
# [Szablony OLE DB](ole-db-templates.md)
## [Szablony konsumentów OLE DB — dokumentacja](ole-db-consumer-templates-reference.md)
### [CAccessor, klasa](caccessor-class.md)
### [CAccessorBase, klasa](caccessorbase-class.md)
#### [CAccessorBase::Close](caccessorbase-close.md)
#### [CAccessorBase::GetHAccessor](caccessorbase-gethaccessor.md)
#### [CAccessorBase::GetNumAccessors](caccessorbase-getnumaccessors.md)
#### [CAccessorBase::IsAutoAccessor](caccessorbase-isautoaccessor.md)
#### [CAccessorBase::ReleaseAccessors](caccessorbase-releaseaccessors.md)
### [CAccessorRowset, klasa](caccessorrowset-class.md)
#### [CAccessorRowset, składowe](caccessorrowset-members.md)
#### [CAccessorRowset, metody](caccessorrowset-methods.md)
#### [CAccessorRowset::Bind](caccessorrowset-bind.md)
#### [CAccessorRowset::CAccessorRowset](caccessorrowset-caccessorrowset.md)
#### [CAccessorRowset::Close](caccessorrowset-close.md)
#### [CAccessorRowset::FreeRecordMemory](caccessorrowset-freerecordmemory.md)
#### [CAccessorRowset::GetColumnInfo](caccessorrowset-getcolumninfo.md)
### [CArrayRowset, klasa](carrayrowset-class.md)
#### [CArrayRowset::CArrayRowset](carrayrowset-carrayrowset.md)
#### [CArrayRowset::m_nRowsRead](carrayrowset-m-nrowsread.md)
#### [CArrayRowset::operator](carrayrowset-operator.md)
#### [CArrayRowset::Snapshot](carrayrowset-snapshot.md)
### [CBookmark, klasa](cbookmark-class.md)
#### [CBookmark::CBookmark](cbookmark-cbookmark.md)
#### [CBookmark::GetBuffer](cbookmark-getbuffer.md)
#### [CBookmark::GetSize](cbookmark-getsize.md)
#### [CBookmark::operator =](cbookmark-operator-equal.md)
#### [CBookmark::SetBookmark](cbookmark-setbookmark.md)
### [CBulkRowset, klasa](cbulkrowset-class.md)
#### [CBulkRowset::AddRefRows](cbulkrowset-addrefrows.md)
#### [CBulkRowset::CBulkRowset](cbulkrowset-cbulkrowset.md)
#### [CBulkRowset::MoveFirst](cbulkrowset-movefirst.md)
#### [CBulkRowset::MoveLast](cbulkrowset-movelast.md)
#### [CBulkRowset::MoveNext](cbulkrowset-movenext.md)
#### [CBulkRowset::MovePrev](cbulkrowset-moveprev.md)
#### [CBulkRowset::MoveToBookmark](cbulkrowset-movetobookmark.md)
#### [CBulkRowset::MoveToRatio](cbulkrowset-movetoratio.md)
#### [CBulkRowset::ReleaseRows](cbulkrowset-releaserows.md)
#### [CBulkRowset::SetRows](cbulkrowset-setrows.md)
### [CColumnAccessor, klasa](ccolumnaccessor-class.md)
### [CCommand, klasa](ccommand-class.md)
#### [CCommand::Close](ccommand-close.md)
#### [CCommand::Create](ccommand-create.md)
#### [CCommand::CreateCommand](ccommand-createcommand.md)
#### [CCommand::GetNextResult](ccommand-getnextresult.md)
#### [CCommand::GetParameterInfo](ccommand-getparameterinfo.md)
#### [CCommand::Open](ccommand-open.md)
#### [CCommand::Prepare](ccommand-prepare.md)
#### [CCommand::ReleaseCommand](ccommand-releasecommand.md)
#### [CCommand::SetParameterInfo](ccommand-setparameterinfo.md)
#### [CCommand::Unprepare](ccommand-unprepare.md)
### [CDataConnection, klasa](cdataconnection-class.md)
#### [CDataConnection::CDataConnection](cdataconnection-cdataconnection.md)
#### [CDataConnection::Copy](cdataconnection-copy.md)
#### [CDataConnection::Open](cdataconnection-open.md)
#### [CDataConnection::OpenNewSession](cdataconnection-opennewsession.md)
#### [CDataConnection::operator, wartość logiczna](cdataconnection-operator-bool.md)
#### [CDataConnection::operator, wartość logiczna (OLE DB)](cdataconnection-operator-bool-ole-db.md)
#### [CDataConnection::operator CDataSource&](cdataconnection-operator-cdatasource-amp.md)
#### [CDataConnection::operator CDataSource*](cdataconnection-operator-cdatasource-star.md)
#### [CDataConnection::operator CSession&](cdataconnection-operator-csession-amp.md)
#### [CDataConnection::operator CSession*](cdataconnection-operator-csession-star.md)
### [CDataSource, klasa](cdatasource-class.md)
#### [CDataSource::Close](cdatasource-close.md)
#### [CDataSource::GetInitializationString](cdatasource-getinitializationstring.md)
#### [CDataSource::GetProperties](cdatasource-getproperties.md)
#### [CDataSource::GetProperty](cdatasource-getproperty.md)
#### [CDataSource::Open](cdatasource-open.md)
#### [CDataSource::OpenFromFileName](cdatasource-openfromfilename.md)
#### [CDataSource::OpenFromInitializationString](cdatasource-openfrominitializationstring.md)
#### [CDataSource::OpenWithPromptFileName](cdatasource-openwithpromptfilename.md)
#### [CDataSource::OpenWithServiceComponents](cdatasource-openwithservicecomponents.md)
### [CDBErrorInfo, klasa](cdberrorinfo-class.md)
#### [CDBErrorInfo::GetAllErrorInfo](cdberrorinfo-getallerrorinfo.md)
#### [CDBErrorInfo::GetBasicErrorInfo](cdberrorinfo-getbasicerrorinfo.md)
#### [CDBErrorInfo::GetCustomErrorObject](cdberrorinfo-getcustomerrorobject.md)
#### [CDBErrorInfo::GetErrorInfo](cdberrorinfo-geterrorinfo.md)
#### [CDBErrorInfo::GetErrorParameters](cdberrorinfo-geterrorparameters.md)
#### [CDBErrorInfo::GetErrorRecords](cdberrorinfo-geterrorrecords.md)
### [CDBPropIDSet, klasa](cdbpropidset-class.md)
#### [CDBPropIDSet::AddPropertyID](cdbpropidset-addpropertyid.md)
#### [CDBPropIDSet::CDBPropIDSet](cdbpropidset-cdbpropidset.md)
#### [CDBPropIDSet::operator =](cdbpropidset-operator-equal.md)
#### [CDBPropIDSet::SetGUID](cdbpropidset-setguid.md)
### [CDBPropSet, klasa](cdbpropset-class.md)
#### [CDBPropSet::AddProperty](cdbpropset-addproperty.md)
#### [CDBPropSet::CDBPropSet](cdbpropset-cdbpropset.md)
#### [CDBPropSet::operator =](cdbpropset-operator-equal.md)
#### [CDBPropSet::SetGUID](cdbpropset-setguid.md)
### [CDynamicAccessor, klasa](cdynamicaccessor-class.md)
#### [CDynamicAccessor::AddBindEntry](cdynamicaccessor-addbindentry.md)
#### [CDynamicAccessor::CDynamicAccessor](cdynamicaccessor-cdynamicaccessor.md)
#### [CDynamicAccessor::Close](cdynamicaccessor-close.md)
#### [CDynamicAccessor::GetBlobHandling](cdynamicaccessor-getblobhandling.md)
#### [CDynamicAccessor::GetBlobSizeLimit](cdynamicaccessor-getblobsizelimit.md)
#### [CDynamicAccessor::GetBookmark](cdynamicaccessor-getbookmark.md)
#### [CDynamicAccessor::GetColumnCount](cdynamicaccessor-getcolumncount.md)
#### [CDynamicAccessor::GetColumnFlags](cdynamicaccessor-getcolumnflags.md)
#### [CDynamicAccessor::GetColumnInfo](cdynamicaccessor-getcolumninfo.md)
#### [CDynamicAccessor::GetColumnName](cdynamicaccessor-getcolumnname.md)
#### [CDynamicAccessor::GetColumnType](cdynamicaccessor-getcolumntype.md)
#### [CDynamicAccessor::GetLength](cdynamicaccessor-getlength.md)
#### [CDynamicAccessor::GetOrdinal](cdynamicaccessor-getordinal.md)
#### [CDynamicAccessor::GetStatus](cdynamicaccessor-getstatus.md)
#### [CDynamicAccessor::GetValue](cdynamicaccessor-getvalue.md)
#### [CDynamicAccessor::SetBlobHandling](cdynamicaccessor-setblobhandling.md)
#### [CDynamicAccessor::SetBlobSizeLimit](cdynamicaccessor-setblobsizelimit.md)
#### [CDynamicAccessor::SetLength](cdynamicaccessor-setlength.md)
#### [CDynamicAccessor::SetStatus](cdynamicaccessor-setstatus.md)
#### [CDynamicAccessor::SetValue](cdynamicaccessor-setvalue.md)
### [CDynamicParameterAccessor, klasa](cdynamicparameteraccessor-class.md)
#### [CDynamicParameterAccessor::CDynamicParameterAccessor](cdynamicparameteraccessor-cdynamicparameteraccessor.md)
#### [CDynamicParameterAccessor::GetParam](cdynamicparameteraccessor-getparam.md)
#### [CDynamicParameterAccessor::GetParamCount](cdynamicparameteraccessor-getparamcount.md)
#### [CDynamicParameterAccessor::GetParamIO](cdynamicparameteraccessor-getparamio.md)
#### [CDynamicParameterAccessor::GetParamLength](cdynamicparameteraccessor-getparamlength.md)
#### [CDynamicParameterAccessor::GetParamName](cdynamicparameteraccessor-getparamname.md)
#### [CDynamicParameterAccessor::GetParamStatus](cdynamicparameteraccessor-getparamstatus.md)
#### [CDynamicParameterAccessor::GetParamString](cdynamicparameteraccessor-getparamstring.md)
#### [CDynamicParameterAccessor::GetParamType](cdynamicparameteraccessor-getparamtype.md)
#### [CDynamicParameterAccessor::SetParam](cdynamicparameteraccessor-setparam.md)
#### [CDynamicParameterAccessor::SetParamLength](cdynamicparameteraccessor-setparamlength.md)
#### [CDynamicParameterAccessor::SetParamStatus](cdynamicparameteraccessor-setparamstatus.md)
#### [CDynamicParameterAccessor::SetParamString](cdynamicparameteraccessor-setparamstring.md)
### [CDynamicStringAccessor, klasa](cdynamicstringaccessor-class.md)
#### [CDynamicStringAccessor::GetString](cdynamicstringaccessor-getstring.md)
#### [CDynamicStringAccessor::SetString](cdynamicstringaccessor-setstring.md)
### [CDynamicStringAccessorA, klasa](cdynamicstringaccessora-class.md)
### [CDynamicStringAccessorW, klasa](cdynamicstringaccessorw-class.md)
### [CEnumerator, klasa](cenumerator-class.md)
#### [CEnumerator::Find](cenumerator-find.md)
#### [CEnumerator::GetMoniker](cenumerator-getmoniker.md)
#### [CEnumerator::Open](cenumerator-open.md)
### [CEnumeratorAccessor, klasa](cenumeratoraccessor-class.md)
#### [CEnumeratorAccessor::m_bIsParent](cenumeratoraccessor-m-bisparent.md)
#### [CEnumeratorAccessor::m_nType](cenumeratoraccessor-m-ntype.md)
#### [CEnumeratorAccessor::m_szDescription](cenumeratoraccessor-m-szdescription.md)
#### [CEnumeratorAccessor::m_szName](cenumeratoraccessor-m-szname.md)
#### [CEnumeratorAccessor::m_szParseName](cenumeratoraccessor-m-szparsename.md)
### [CManualAccessor, klasa](cmanualaccessor-class.md)
#### [CManualAccessor::AddBindEntry](cmanualaccessor-addbindentry.md)
#### [CManualAccessor::AddParameterEntry](cmanualaccessor-addparameterentry.md)
#### [CManualAccessor::CreateAccessor](cmanualaccessor-createaccessor.md)
#### [CManualAccessor::CreateParameterAccessor](cmanualaccessor-createparameteraccessor.md)
### [CMultipleResults, klasa](cmultipleresults-class.md)
### [CNoAccessor, klasa](cnoaccessor-class.md)
### [CNoMultipleResults, klasa](cnomultipleresults-class.md)
### [CNoRowset, klasa](cnorowset-class.md)
### [CRestrictions, klasa](crestrictions-class.md)
#### [CRestrictions::Open](crestrictions-open.md)
### [CRowset, klasa](crowset-class.md)
#### [CRowset::AddRefRows](crowset-addrefrows.md)
#### [CRowset::Close](crowset-close.md)
#### [CRowset::Compare](crowset-compare.md)
#### [CRowset::CRowset](crowset-crowset.md)
#### [CRowset::Delete](crowset-delete.md)
#### [CRowset::FindNextRow](crowset-findnextrow.md)
#### [CRowset::GetApproximatePosition](crowset-getapproximateposition.md)
#### [CRowset::GetData](crowset-getdata.md)
#### [CRowset::GetDataHere](crowset-getdatahere.md)
#### [CRowset::GetOriginalData](crowset-getoriginaldata.md)
#### [CRowset::GetRowStatus](crowset-getrowstatus.md)
#### [CRowset::Insert](crowset-insert.md)
#### [CRowset::IsSameRow](crowset-issamerow.md)
#### [CRowset::MoveFirst](crowset-movefirst.md)
#### [CRowset::MoveLast](crowset-movelast.md)
#### [CRowset::MoveNext](crowset-movenext.md)
#### [CRowset::MovePrev](crowset-moveprev.md)
#### [CRowset::MoveToBookmark](crowset-movetobookmark.md)
#### [CRowset::MoveToRatio](crowset-movetoratio.md)
#### [CRowset::ReleaseRows](crowset-releaserows.md)
#### [CRowset::SetData](crowset-setdata.md)
#### [CRowset::Undo](crowset-undo.md)
#### [CRowset::Update](crowset-update.md)
#### [CRowset::UpdateAll](crowset-updateall.md)
### [CSession, klasa](csession-class.md)
#### [CSession::Abort](csession-abort.md)
#### [CSession::Close](csession-close.md)
#### [CSession::Commit](csession-commit.md)
#### [CSession::GetTransactionInfo](csession-gettransactioninfo.md)
#### [CSession::Open](csession-open.md)
#### [CSession::StartTransaction](csession-starttransaction.md)
### [CStreamRowset, klasa](cstreamrowset-class.md)
#### [CStreamRowset::Close](cstreamrowset-close.md)
#### [CStreamRowset::CStreamRowset](cstreamrowset-cstreamrowset.md)
### [CTable, klasa](ctable-class.md)
#### [CTable::Open](ctable-open.md)
### [CXMLAccessor, klasa](cxmlaccessor-class.md)
#### [CXMLAccessor::GetXMLColumnData](cxmlaccessor-getxmlcolumndata.md)
#### [CXMLAccessor::GetXMLRowData](cxmlaccessor-getxmlrowdata.md)
### [IRowsetNotifyImpl, klasa](irowsetnotifyimpl-class.md)
#### [IRowsetNotifyImpl::OnFieldChange](irowsetnotifyimpl-onfieldchange.md)
#### [IRowsetNotifyImpl::OnRowChange](irowsetnotifyimpl-onrowchange.md)
#### [IRowsetNotifyImpl::OnRowsetChange](irowsetnotifyimpl-onrowsetchange.md)
### [Klasy zestawów wierszy schematu i klasy Typedef](schema-rowset-classes-and-typedef-classes.md)
#### [CAssertions, CAssertionInfo](cassertions-cassertioninfo.md)
#### [CCatalogs, CCatalogInfo](ccatalogs-ccataloginfo.md)
#### [CCharacterSets, CCharacterSetInfo](ccharactersets-ccharactersetinfo.md)
#### [CCheckConstraints, CCheckConstraintInfo](ccheckconstraints-ccheckconstraintinfo.md)
#### [CCollations, CCollationInfo](ccollations-ccollationinfo.md)
#### [CColumnDomainUsage, CColumnDomainUsageInfo](ccolumndomainusage-ccolumndomainusageinfo.md)
#### [CColumnPrivileges, CColumnPrivilegeInfo](ccolumnprivileges-ccolumnprivilegeinfo.md)
#### [CColumns, CColumnsInfo](ccolumns-ccolumnsinfo.md)
#### [CConstraintColumnUsage, CConstraintColumnUsageInfo](cconstraintcolumnusage-cconstraintcolumnusageinfo.md)
#### [CConstraintTableUsage, CConstraintTableUsageInfo](cconstrainttableusage-cconstrainttableusageinfo.md)
#### [CForeignKeys, CForeignKeysInfo](cforeignkeys-cforeignkeysinfo.md)
#### [CIndexes, CIndexInfo](cindexes-cindexinfo.md)
#### [CKeyColumns, CKeyColumnInfo](ckeycolumns-ckeycolumninfo.md)
#### [CPrimaryKeys, CPrimaryKeyInfo](cprimarykeys-cprimarykeyinfo.md)
#### [CProcedureColumns, CProcedureColumnInfo](cprocedurecolumns-cprocedurecolumninfo.md)
#### [CProcedureParameters CProcedureParamInfo](cprocedureparameters-cprocedureparaminfo.md)
#### [CProcedures, CProcedureInfo](cprocedures-cprocedureinfo.md)
#### [CProviderTypes, CProviderInfo](cprovidertypes-cproviderinfo.md)
#### [CReferentialConstraints, CReferentialConstraintInfo](creferentialconstraints-creferentialconstraintinfo.md)
#### [CSchemata, CSchemataInfo](cschemata-cschematainfo.md)
#### [CSQLLanguages, CSQLLanguageInfo](csqllanguages-csqllanguageinfo.md)
#### [CStatistics, CStatisticInfo](cstatistics-cstatisticinfo.md)
#### [CTableConstraints, CTableConstraintInfo](ctableconstraints-ctableconstraintinfo.md)
#### [CTablePrivileges, CTablePrivilegeInfo](ctableprivileges-ctableprivilegeinfo.md)
#### [CTables, CTableInfo](ctables-ctableinfo.md)
#### [CTranslations, CTranslationInfo](ctranslations-ctranslationinfo.md)
#### [CUsagePrivileges, CUsagePrivilegeInfo](cusageprivileges-cusageprivilegeinfo.md)
#### [CViewColumnUsage, CViewColumnInfo](cviewcolumnusage-cviewcolumninfo.md)
#### [CViews, CViewInfo](cviews-cviewinfo.md)
#### [CViewTableUsage, CViewTableInfo](cviewtableusage-cviewtableinfo.md)
### [Makra i funkcje globalne dla szablonów konsumentów OLE DB](macros-and-global-functions-for-ole-db-consumer-templates.md)
#### [AtlTraceErrorRecords](atltraceerrorrecords.md)
#### [BEGIN_ACCESSOR](begin-accessor.md)
#### [BEGIN_ACCESSOR_MAP](begin-accessor-map.md)
#### [BEGIN_COLUMN_MAP](begin-column-map.md)
#### [BEGIN_PARAM_MAP](begin-param-map.md)
#### [BLOB_ENTRY](blob-entry.md)
#### [BLOB_ENTRY_LENGTH](blob-entry-length.md)
#### [BLOB_ENTRY_LENGTH_STATUS](blob-entry-length-status.md)
#### [BLOB_ENTRY_STATUS](blob-entry-status.md)
#### [BLOB_NAME](blob-name.md)
#### [BLOB_NAME_LENGTH](blob-name-length.md)
#### [BLOB_NAME_LENGTH_STATUS](blob-name-length-status.md)
#### [BLOB_NAME_STATUS](blob-name-status.md)
#### [BOOKMARK_ENTRY](bookmark-entry.md)
#### [COLUMN_ENTRY](column-entry.md)
#### [COLUMN_ENTRY_EX](column-entry-ex.md)
#### [COLUMN_ENTRY_LENGTH](column-entry-length.md)
#### [COLUMN_ENTRY_LENGTH_STATUS](column-entry-length-status.md)
#### [COLUMN_ENTRY_PS](column-entry-ps.md)
#### [COLUMN_ENTRY_PS_LENGTH](column-entry-ps-length.md)
#### [COLUMN_ENTRY_PS_LENGTH_STATUS](column-entry-ps-length-status.md)
#### [COLUMN_ENTRY_PS_STATUS](column-entry-ps-status.md)
#### [COLUMN_ENTRY_STATUS](column-entry-status.md)
#### [COLUMN_ENTRY_TYPE](column-entry-type.md)
#### [COLUMN_ENTRY_TYPE_SIZE](column-entry-type-size.md)
#### [COLUMN_NAME](column-name.md)
#### [COLUMN_NAME_EX](column-name-ex.md)
#### [COLUMN_NAME_LENGTH](column-name-length.md)
#### [COLUMN_NAME_LENGTH_STATUS](column-name-length-status.md)
#### [COLUMN_NAME_PS](column-name-ps.md)
#### [COLUMN_NAME_PS_LENGTH](column-name-ps-length.md)
#### [COLUMN_NAME_PS_LENGTH_STATUS](column-name-ps-length-status.md)
#### [COLUMN_NAME_PS_STATUS](column-name-ps-status.md)
#### [COLUMN_NAME_STATUS](column-name-status.md)
#### [COLUMN_NAME_TYPE](column-name-type.md)
#### [COLUMN_NAME_TYPE_PS](column-name-type-ps.md)
#### [COLUMN_NAME_TYPE_SIZE](column-name-type-size.md)
#### [COLUMN_NAME_TYPE_STATUS](column-name-type-status.md)
#### [DEFINE_COMMAND](define-command.md)
#### [DEFINE_COMMAND_EX](define-command-ex.md)
#### [END_ACCESSOR](end-accessor.md)
#### [END_ACCESSOR_MAP](end-accessor-map.md)
#### [END_COLUMN_MAP](end-column-map.md)
#### [END_PARAM_MAP](end-param-map.md)
#### [SET_PARAM_TYPE](set-param-type.md)
## [Szablony dostawców OLE DB — dokumentacja](ole-db-provider-templates-reference.md)
### [CRowsetImpl, klasa](crowsetimpl-class.md)
#### [CRowsetImpl::GetColumnInfo](crowsetimpl-getcolumninfo.md)
#### [CRowsetImpl::GetCommandFromID](crowsetimpl-getcommandfromid.md)
#### [CRowsetImpl::m_rgRowData](crowsetimpl-m-rgrowdata.md)
#### [CRowsetImpl::m_strCommandText](crowsetimpl-m-strcommandtext.md)
#### [CRowsetImpl::m_strIndexText](crowsetimpl-m-strindextext.md)
#### [CRowsetImpl::NameFromDBID](crowsetimpl-namefromdbid.md)
#### [CRowsetImpl::SetCommandText](crowsetimpl-setcommandtext.md)
#### [CRowsetImpl::ValidateCommandID](crowsetimpl-validatecommandid.md)
### [CSimpleRow, klasa](csimplerow-class.md)
#### [CSimpleRow::AddRefRow](csimplerow-addrefrow.md)
#### [CSimpleRow::Compare](csimplerow-compare.md)
#### [CSimpleRow::CSimpleRow](csimplerow-csimplerow.md)
#### [CSimpleRow::m_dwRef](csimplerow-m-dwref.md)
#### [CSimpleRow::m_iRowset](csimplerow-m-irowset.md)
#### [CSimpleRow::ReleaseRow](csimplerow-releaserow.md)
### [CUtlProps, klasa](cutlprops-class.md)
#### [CUtlProps::GetPropValue](cutlprops-getpropvalue.md)
#### [CUtlProps::IsValidValue](cutlprops-isvalidvalue.md)
#### [CUtlProps::OnInterfaceRequested](cutlprops-oninterfacerequested.md)
#### [CUtlProps::OnPropertyChanged](cutlprops-onpropertychanged.md)
#### [CUtlProps::SetPropValue](cutlprops-setpropvalue.md)
### [IAccessorImpl, klasa](iaccessorimpl-class.md)
#### [IAccessorImpl::AddRefAccessor](iaccessorimpl-addrefaccessor.md)
#### [IAccessorImpl::CreateAccessor](iaccessorimpl-createaccessor.md)
#### [IAccessorImpl::GetBindings](iaccessorimpl-getbindings.md)
#### [IAccessorImpl::IAccessorImpl](iaccessorimpl-iaccessorimpl.md)
#### [IAccessorImpl::ReleaseAccessor](iaccessorimpl-releaseaccessor.md)
### [IColumnsInfoImpl, klasa](icolumnsinfoimpl-class.md)
#### [IColumnsInfoImpl::GetColumnInfo](icolumnsinfoimpl-getcolumninfo.md)
#### [IColumnsInfoImpl::MapColumnIDs](icolumnsinfoimpl-mapcolumnids.md)
### [ICommandImpl, klasa](icommandimpl-class.md)
#### [ICommandImpl::Cancel](icommandimpl-cancel.md)
#### [ICommandImpl::CancelExecution](icommandimpl-cancelexecution.md)
#### [ICommandImpl::CreateRowset](icommandimpl-createrowset.md)
#### [ICommandImpl::Execute](icommandimpl-execute.md)
#### [ICommandImpl::GetDBSession](icommandimpl-getdbsession.md)
#### [ICommandImpl::ICommandImpl](icommandimpl-icommandimpl.md)
#### [ICommandImpl::m_bCancel](icommandimpl-m-bcancel.md)
#### [ICommandImpl::m_bCancelWhenExecuting](icommandimpl-m-bcancelwhenexecuting.md)
#### [ICommandImpl::m_bIsExecuting](icommandimpl-m-bisexecuting.md)
### [ICommandPropertiesImpl, klasa](icommandpropertiesimpl-class.md)
#### [ICommandPropertiesImpl::GetProperties](icommandpropertiesimpl-getproperties.md)
#### [ICommandPropertiesImpl::SetProperties](icommandpropertiesimpl-setproperties.md)
### [ICommandTextImpl, klasa](icommandtextimpl-class.md)
#### [ICommandTextImpl::GetCommandText](icommandtextimpl-getcommandtext.md)
#### [ICommandTextImpl::m_strCommandText](icommandtextimpl-m-strcommandtext.md)
#### [ICommandTextImpl::SetCommandText](icommandtextimpl-setcommandtext.md)
### [IConvertTypeImpl, klasa](iconverttypeimpl-class.md)
#### [IConvertTypeImpl::CanConvert](iconverttypeimpl-canconvert.md)
### [IDBCreateCommandImpl, klasa](idbcreatecommandimpl-class.md)
#### [IDBCreateCommandImpl::CreateCommand](idbcreatecommandimpl-createcommand.md)
### [IDBCreateSessionImpl, klasa](idbcreatesessionimpl-class.md)
#### [IDBCreateSessionImpl::CreateSession](idbcreatesessionimpl-createsession.md)
### [IDBInitializeImpl, klasa](idbinitializeimpl-class.md)
#### [IDBInitializeImpl::IDBInitializeImpl](idbinitializeimpl-idbinitializeimpl.md)
#### [IDBInitializeImpl::Initialize](idbinitializeimpl-initialize.md)
#### [IDBInitializeImpl::m_dwStatus](idbinitializeimpl-m-dwstatus.md)
#### [IDBInitializeImpl::m_pCUtlPropInfo](idbinitializeimpl-m-pcutlpropinfo.md)
#### [IDBInitializeImpl::Uninitialize](idbinitializeimpl-uninitialize.md)
### [IDBPropertiesImpl, klasa](idbpropertiesimpl-class.md)
#### [IDBPropertiesImpl::GetProperties](idbpropertiesimpl-getproperties.md)
#### [IDBPropertiesImpl::GetPropertyInfo](idbpropertiesimpl-getpropertyinfo.md)
#### [IDBPropertiesImpl::SetProperties](idbpropertiesimpl-setproperties.md)
### [IDBSchemaRowsetImpl, klasa](idbschemarowsetimpl-class.md)
#### [IDBSchemaRowsetImpl::CheckRestrictions](idbschemarowsetimpl-checkrestrictions.md)
#### [IDBSchemaRowsetImpl::CreateSchemaRowset](idbschemarowsetimpl-createschemarowset.md)
#### [IDBSchemaRowsetImpl::GetRowset](idbschemarowsetimpl-getrowset.md)
#### [IDBSchemaRowsetImpl::GetSchemas](idbschemarowsetimpl-getschemas.md)
#### [IDBSchemaRowsetImpl::SetRestrictions](idbschemarowsetimpl-setrestrictions.md)
### [IErrorRecordsImpl, klasa](ierrorrecordsimpl-class.md)
#### [IErrorRecordsImpl::AddErrorRecord](ierrorrecordsimpl-adderrorrecord.md)
#### [IErrorRecordsImpl::GetBasicErrorInfo](ierrorrecordsimpl-getbasicerrorinfo.md)
#### [IErrorRecordsImpl::GetCustomErrorObject](ierrorrecordsimpl-getcustomerrorobject.md)
#### [IErrorRecordsImpl::GetErrorDescriptionString](ierrorrecordsimpl-geterrordescriptionstring.md)
#### [IErrorRecordsImpl::GetErrorGUID](ierrorrecordsimpl-geterrorguid.md)
#### [IErrorRecordsImpl::GetErrorHelpContext](ierrorrecordsimpl-geterrorhelpcontext.md)
#### [IErrorRecordsImpl::GetErrorHelpFile](ierrorrecordsimpl-geterrorhelpfile.md)
#### [IErrorRecordsImpl::GetErrorInfo](ierrorrecordsimpl-geterrorinfo.md)
#### [IErrorRecordsImpl::GetErrorParameters](ierrorrecordsimpl-geterrorparameters.md)
#### [IErrorRecordsImpl::GetRecordCount](ierrorrecordsimpl-getrecordcount.md)
#### [IErrorRecordsImpl::GetErrorSource](ierrorrecordsimpl-geterrorsource.md)
#### [IErrorRecordsImpl::m_rgErrors](ierrorrecordsimpl-m-rgerrors.md)
### [IGetDataSourceImpl, klasa](igetdatasourceimpl-class.md)
#### [IGetDataSourceImpl::GetDataSource](igetdatasourceimpl-getdatasource.md)
### [IOpenRowsetImpl, klasa](iopenrowsetimpl-class.md)
#### [IOpenRowsetImpl::CreateRowset](iopenrowsetimpl-createrowset.md)
#### [IOpenRowsetImpl::OpenRowset](iopenrowsetimpl-openrowset.md)
### [IRowsetChangeImpl, klasa](irowsetchangeimpl-class.md)
#### [IRowsetChangeImpl::DeleteRows](irowsetchangeimpl-deleterows.md)
#### [IRowsetChangeImpl::FlushData](irowsetchangeimpl-flushdata.md)
#### [IRowsetChangeImpl::InsertRow](irowsetchangeimpl-insertrow.md)
#### [IRowsetChangeImpl::SetData](irowsetchangeimpl-setdata.md)
### [IRowsetCreatorImpl, klasa](irowsetcreatorimpl-class.md)
#### [IRowsetCreatorImpl::SetSite](irowsetcreatorimpl-setsite.md)
### [IRowsetIdentityImpl, klasa](irowsetidentityimpl-class.md)
#### [IRowsetIdentityImpl::IsSameRow](irowsetidentityimpl-issamerow.md)
### [IRowsetImpl, klasa](irowsetimpl-class.md)
#### [IRowsetImpl::AddRefRows](irowsetimpl-addrefrows.md)
#### [IRowsetImpl::CreateRow](irowsetimpl-createrow.md)
#### [IRowsetImpl::GetData](irowsetimpl-getdata.md)
#### [IRowsetImpl::GetDBStatus](irowsetimpl-getdbstatus.md)
#### [IRowsetImpl::GetNextRows](irowsetimpl-getnextrows.md)
#### [IRowsetImpl::IRowsetImpl](irowsetimpl-irowsetimpl.md)
#### [IRowsetImpl::m_bCanFetchBack](irowsetimpl-m-bcanfetchback.md)
#### [IRowsetImpl::m_bCanScrollBack](irowsetimpl-m-bcanscrollback.md)
#### [IRowsetImpl::m_bReset](irowsetimpl-m-breset.md)
#### [IRowsetImpl::m_iRowset](irowsetimpl-m-irowset.md)
#### [IRowsetImpl::m_rgRowHandles](irowsetimpl-m-rgrowhandles.md)
#### [IRowsetImpl::RefRows](irowsetimpl-refrows.md)
#### [IRowsetImpl::ReleaseRows](irowsetimpl-releaserows.md)
#### [IRowsetImpl::RestartPosition](irowsetimpl-restartposition.md)
#### [IRowsetImpl::SetDBStatus](irowsetimpl-setdbstatus.md)
### [IRowsetInfoImpl, klasa](irowsetinfoimpl-class.md)
#### [IRowsetInfoImpl::GetProperties](irowsetinfoimpl-getproperties.md)
#### [IRowsetInfoImpl::GetReferencedRowset](irowsetinfoimpl-getreferencedrowset.md)
#### [IRowsetInfoImpl::GetSpecification](irowsetinfoimpl-getspecification.md)
### [IRowsetLocateImpl, klasa](irowsetlocateimpl-class.md)
#### [IRowsetLocateImpl::Compare](irowsetlocateimpl-compare.md)
#### [IRowsetLocateImpl::GetRowsAt](irowsetlocateimpl-getrowsat.md)
#### [IRowsetLocateImpl::GetRowsByBookmark](irowsetlocateimpl-getrowsbybookmark.md)
#### [IRowsetLocateImpl::Hash](irowsetlocateimpl-hash.md)
#### [IRowsetLocateImpl::m_rgBookmarks](irowsetlocateimpl-m-rgbookmarks.md)
### [IRowsetNotifyCP, klasa](irowsetnotifycp-class.md)
#### [IRowsetNotifyCP::Fire_OnFieldChange](irowsetnotifycp-fire-onfieldchange.md)
#### [IRowsetNotifyCP::Fire_OnRowChange](irowsetnotifycp-fire-onrowchange.md)
#### [IRowsetNotifyCP::Fire_OnRowsetChange](irowsetnotifycp-fire-onrowsetchange.md)
### [IRowsetUpdateImpl, klasa](irowsetupdateimpl-class.md)
#### [IRowsetUpdateImpl::GetPendingRows](irowsetupdateimpl-getpendingrows.md)
#### [IRowsetUpdateImpl::GetOriginalData](irowsetupdateimpl-getoriginaldata.md)
#### [IRowsetUpdateImpl::GetRowStatus](irowsetupdateimpl-getrowstatus.md)
#### [IRowsetUpdateImpl::IsUpdateAllowed](irowsetupdateimpl-isupdateallowed.md)
#### [IRowsetUpdateImpl::m_mapCachedData](irowsetupdateimpl-m-mapcacheddata.md)
#### [IRowsetUpdateImpl::SetData](irowsetupdateimpl-setdata.md)
#### [IRowsetUpdateImpl::Undo](irowsetupdateimpl-undo.md)
#### [IRowsetUpdateImpl::Update](irowsetupdateimpl-update.md)
### [ISessionPropertiesImpl, klasa](isessionpropertiesimpl-class.md)
#### [ISessionPropertiesImpl::GetProperties](isessionpropertiesimpl-getproperties.md)
#### [ISessionPropertiesImpl::SetProperties](isessionpropertiesimpl-setproperties.md)
### [Makra dla szablonów dostawców OLE DB](macros-for-ole-db-provider-templates.md)
#### [BEGIN_PROPERTY_SET](begin-property-set.md)
#### [BEGIN_PROPERTY_SET_EX](begin-property-set-ex.md)
#### [BEGIN_PROPSET_MAP](begin-propset-map.md)
#### [BEGIN_PROVIDER_COLUMN_MAP](begin-provider-column-map.md)
#### [BEGIN_SCHEMA_MAP](begin-schema-map.md)
#### [CHAIN_PROPERTY_SET](chain-property-set.md)
#### [END_PROPERTY_SET](end-property-set.md)
#### [END_PROPSET_MAP](end-propset-map.md)
#### [END_PROVIDER_COLUMN_MAP](end-provider-column-map.md)
#### [END_SCHEMA_MAP](end-schema-map.md)
#### [PROVIDER_COLUMN_ENTRY](provider-column-entry.md)
#### [PROVIDER_COLUMN_ENTRY_GN](provider-column-entry-gn.md)
#### [PROVIDER_COLUMN_ENTRY_FIXED](provider-column-entry-fixed.md)
#### [PROVIDER_COLUMN_ENTRY_LENGTH](provider-column-entry-length.md)
#### [PROVIDER_COLUMN_ENTRY_STR](provider-column-entry-str.md)
#### [PROVIDER_COLUMN_ENTRY_TYPE_LENGTH](provider-column-entry-type-length.md)
#### [PROVIDER_COLUMN_ENTRY_WSTR](provider-column-entry-wstr.md)
#### [PROPERTY_INFO_ENTRY](property-info-entry.md)
#### [PROPERTY_INFO_ENTRY_EX](property-info-entry-ex.md)
#### [PROPERTY_INFO_ENTRY_VALUE](property-info-entry-value.md)
#### [SCHEMA_ENTRY](schema-entry.md)