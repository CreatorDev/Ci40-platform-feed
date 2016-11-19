#!/usr/bin/env groovy

def DEFAULT_OPENWRT_BRANCH = 'ci40'

properties([
    parameters([
        string(defaultValue: DEFAULT_OPENWRT_BRANCH, description: 'OpenWrt branch to test against',
            name: "OPENWRT_BRANCH")
    ])
])

stage('Trigger openwrt build') {
    build job: "../openwrt/${OPENWRT_BRANCH ?: DEFAULT_OPENWRT_BRANCH}", parameters: [
        string(name: 'OVERRIDE_CI40-PLATFORM-FEED', value: "${BRANCH_NAME}")
    ]
}
