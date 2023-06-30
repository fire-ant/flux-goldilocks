load('ext://helm_resource', 'helm_resource', 'helm_repo')


k8s_yaml(
    './flux/ns.yaml'
    )

# flux
helm_repo(
    'fluxcd-community',
    'https://fluxcd-community.github.io/helm-charts',
    labels=['flux-repo'],
    resource_name='flux-repo'
    )
helm_resource(
    name= 'flux2',
    chart='fluxcd-community/flux2',
    namespace='flux-system',
    flags=['--values=./flux/values.yaml'],
    resource_deps=['flux-repo', 'flux-ns']
    )

# goldilocks
helm_repo(
    'fairwinds-stable',
    'https://charts.fairwinds.com/stable',
    labels=['golidlocks-repo'],
    resource_name='goldilocks-repo'
)
helm_resource(
    name= 'goldilocks',
    chart='fairwinds-stable/goldilocks',
    namespace='goldilocks',
    flags=['--create-namespace','--values=./fairwinds/goldilocks/values.yaml'],
    resource_deps=['goldilocks-repo']
)
# vpa
helm_resource(
    name= 'vpa',
    chart='fairwinds-stable/vpa',
    namespace='vpa-system',
    flags=['--create-namespace','--values=./fairwinds/vpa/values.yaml'],
    resource_deps=['goldilocks-repo']
)

k8s_yaml(
    './fairwinds/vpa/config.yaml'
    )
