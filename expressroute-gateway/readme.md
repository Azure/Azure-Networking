## Configuration backup for ExpressRoute Gateway, ExpressRoute Gateway Connection, and Routing Table Associated with Gateway (if any).

Backup configuration using Azure powershell:

```powershell
$ Connect-AzAccount
$ resourceGroupName = "YourResourceGroupName"
$ gatewayName = "YourGatewayName"
$routeTableName = "YourRouteTableName"
$ backupGW = "C:\Path\To\Backup\gatewayConfig.json"
$ backupGWConn = "C:\Path\To\Backup\gatewayConnConfig.json"
$ backupRT = "C:\Path\To\Backup\routeTableConfig.json"

$ gateway = Get-AzVirtualNetworkGateway -ResourceGroupName $resourceGroupName -Name $gatewayName
$ connections = Get-AzVirtualNetworkGatewayConnection -ResourceGroupName $resourceGroupName
$ routeTable = Get-AzRouteTable -ResourceGroupName $resourceGroupName -Name $routeTableName
$ gatewayConfig = $gateway | ConvertTo-Json -Depth 10
$ connectionsConfig = $connections | ConvertTo-Json -Depth 10
$ routeTableConfig = $routeTable | ConvertTo-Json -Depth 10

$ Set-Content -Path $backupGW -Value $gatewayConfig
$ Get-Content -Path $backupGW
$ Set-Content -Path $backupGWConn -Value $gatewayConfig
$ Get-Content -Path $backupGWConn
$ Set-Content -Path $backupFilePath -Value $connectionsConfig
$ Get-Content -Path $backupFilePath
