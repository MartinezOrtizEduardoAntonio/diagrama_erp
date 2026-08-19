```mermaid
graph LR
    Activities["Activities"]
    Customer["Customer"]
    Lead["Lead"]
    Supplier["Supplier"]
    BusinessPartnerMaster["Business Partner Master"]
    
    Activities --> Customer
    Customer --> Lead
    Customer --> Supplier
    Supplier --> BusinessPartnerMaster
    
    Customer -->|Opportunity| Pricing["Pricing"]
    Pricing -->|Purchase Request| PurchaseQuotation["Purchase Quotation"]
    Pricing -->|Sales Quotation| SalesQuotation["Sales Quotation"]
    
    SalesQuotation -->|Sales Order| SalesOrder["Sales Order"]
    PurchaseQuotation -->|Purchase Order| PurchaseOrder["Purchase Order"]
    
    SalesOrder -->|Item Master| ItemMaster["Item Master"]
    SalesOrder -->|Warehouse Management| WarehouseManagement["Warehouse Management"]
    PurchaseOrder -->|Sourcing| Sourcing["Sourcing"]
    
    ItemMaster -->|Production Order| ProductionOrder["Production Order"]
    WarehouseManagement -->|Production Order| ProductionOrder
    Sourcing -->|Material Requirements Planning| MaterialRequirementsPlanning["Material Requirements Planning"]
    
    SalesOrder -->|Delivery Note| DeliveryNote["Delivery Note"]
    ProductionOrder -->|Issue to Production| IssueToProduction["Issue to Production"]
    PurchaseOrder -->|Goods Receipt PO| GoodsReceiptPO["Goods Receipt PO"]
    
    MaterialRequirementsPlanning -->|Demand Planning| DemandPlanning["Demand Planning"]
    DemandPlanning -->|Backorder Reporting| BackorderReporting["Backorder Reporting"]
    
    DeliveryNote -->|Service Call| ServiceCall["Service Call"]
    ServiceCall -->|Service Contract| ServiceContract["Service Contract"]
    ServiceContract -->|Service Billing| ServiceBilling["Service Billing"]
    
    GoodsReceiptPO -->|Financial Postings| FinancialPostings["Financial Postings"]
    IssueToProduction -->|Receipt from Production| ReceiptFromProduction["Receipt from Production"]
    ReceiptFromProduction -->|Financial Postings| FinancialPostings
    
    BackorderReporting -->|Inventory Audit Report| InventoryAuditReport["Inventory Audit Report"]
    FinancialPostings -->|Journal Entries| JournalEntries["Journal Entries"]
    
    JournalEntries -->|AP/AR| APAR["AP/AR"]
    APAR -->|Cash Management| CashManagement["Cash Management"]
    CashManagement -->|Reconciliation| Reconciliation["Reconciliation"]
    Reconciliation -->|Financial Reporting| FinancialReporting["Financial Reporting"]
    
    JournalEntries -->|AR Invoice| ARInvoice["AR Invoice"]
    ARInvoice -->|Incoming Payments| IncomingPayments["Incoming Payments"]
    IncomingPayments -->|Outgoing Payments| OutgoingPayments["Outgoing Payments"]
    
    InventoryAuditReport -->|Account Balances Report| AccountBalancesReport["Account Balances Report"]
    
    Sourcing -->|Chart of Accounts| ChartOfAccounts["Chart of Accounts"]
    ChartOfAccounts -->|General Ledger Accounts| GeneralLedgerAccounts["General Ledger Accounts"]
    GeneralLedgerAccounts -->|G/L Account Determination| GLAccountDetermination["G/L Account Determination"]
    GLAccountDetermination -->|Cost Accounting| CostAccounting["Cost Accounting"]
    
    CostAccounting -->|Bill of Materials| BillOfMaterials["Bill of Materials"]
    
    OutgoingPayments -->|Product Reporting| ProductReporting["Product Reporting"]
    FinancialReporting -->|Product Reporting| ProductReporting
    
    classDef crmSRM fill:#4ade80,stroke:#16a34a,color:#fff
    classDef service fill:#facc15,stroke:#ca8a04,color:#000
    classDef sales fill:#fb923c,stroke:#d97706,color:#fff
    classDef inventory fill:#6b7280,stroke:#374151,color:#fff
    classDef purchasing fill:#3b82f6,stroke:#1d4ed8,color:#fff
    classDef finance fill:#ef4444,stroke:#b91c1c,color:#fff
    classDef production fill:#6b21a8,stroke:#581c87,color:#fff
    classDef reporting fill:#ec4899,stroke:#be185d,color:#fff
    
    class Customer,Lead,Supplier,BusinessPartnerMaster,Opportunity,Pricing crmSRM
    class ServiceCall,ServiceContract,ServiceBilling service
    class SalesQuotation,SalesOrder,DeliveryNote sales
    class ItemMaster,WarehouseManagement,InventoryAuditReport inventory
    class PurchaseQuotation,PurchaseOrder,GoodsReceiptPO,Sourcing purchasing
    class FinancialPostings,JournalEntries,APAR,CashManagement,Reconciliation,ARInvoice,IncomingPayments,OutgoingPayments,FinancialReporting,ChartOfAccounts,GeneralLedgerAccounts,GLAccountDetermination,CostAccounting finance
    class ProductionOrder,IssueToProduction,ReceiptFromProduction,MaterialRequirementsPlanning,DemandPlanning,BillOfMaterials production
    class AccountBalancesReport,ProductReporting reporting
