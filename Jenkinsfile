#!/usr/bin/env groovy

properties([
    parameters([
        string(defaultValue: 'ci40', description: 'OpenWrt branch to test against', \
            name: "OPENWRT_BRANCH")
    ])
])

stage('Trigger openwrt build') {
    build job: "../openwrt/${OPENWRT_BRANCH}", parameters: [
        string(name: 'OVERRIDE_CI40-PLATFORM-FEED', value: "${BRANCH_NAME}")
    ]
}
