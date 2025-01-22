# ローカルにnginxのサンプルを構築:

```bash
kubectl apply -f https://raw.githubusercontent.com/koh-sh/k8s-tutorial/refs/heads/main/nginx-deployment.yml
```

```bash
curl localhost:30080
```

# Kubernetesの主要なkubectlコマンド

リソースの作成・更新・削除：
```bash
kubectl apply -f <ファイル名>.yaml    # マニフェストからリソースを作成/更新
kubectl delete -f <ファイル名>.yaml    # マニフェストで定義されたリソースを削除
kubectl create deployment nginx --image=nginx  # デプロイメントを直接作成
```

リソースの表示・確認：
```bash
kubectl get pods                      # Podの一覧表示
kubectl get pods -o wide              # Pod一覧の詳細表示
kubectl get all                       # すべてのリソース表示
kubectl describe pod <Pod名>          # Podの詳細情報表示
kubectl logs <Pod名>                  # Podのログを表示
```

デバッグ・トラブルシューティング：
```bash
kubectl exec -it <Pod名> -- /bin/bash  # Podの中でシェルを実行
kubectl port-forward <Pod名> 8080:80    # ローカルPCとPod間でポートフォワード
kubectl top pods                        # Podのリソース使用状況確認
```

コンテキストとネームスペース：
```bash
kubectl config get-contexts            # 利用可能なコンテキスト一覧
kubectl config use-context <名前>      # コンテキストの切り替え
kubectl get ns                         # ネームスペース一覧
kubectl create ns <名前>               # ネームスペース作成
```

スケーリング：
```bash
kubectl scale deployment <名前> --replicas=3  # レプリカ数を変更
kubectl rollout restart deployment <名前>     # デプロイメントを再起動
kubectl rollout history deployment <名前>     # デプロイメント履歴確認
```

リソースの編集：
```bash
kubectl edit deployment <名前>         # デプロイメントを直接編集
kubectl patch deployment <名前> -p '{"spec": {"replicas": 3}}'  # 部分的な更新
```

これらのコマンドはよく使用される基本的なものです。必要に応じて`kubectl help`や`kubectl <コマンド> --help`で詳細なヘルプを確認できます。
