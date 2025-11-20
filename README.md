//
//  SilverTrace.swift
//

import Foundation

struct SystemSnapshot {
    let cpuUsage: Double
    let memoryUsage: Double
}

final class SilverTrace {
    
    func start() {
        Timer.scheduledTimer(withTimeInterval: 1, repeats: true) { _ in
            let snap = self.collectSnapshot()
            print("CPU: \(snap.cpuUsage)% | MEM: \(snap.memoryUsage)%")
        }
        RunLoop.main.run()
    }
    
    private func collectSnapshot() -> SystemSnapshot {
        let cpu = Double.random(in: 1...80)
        let mem = Double.random(in: 10...90)
        return SystemSnapshot(cpuUsage: cpu, memoryUsage: mem)
    }
}

SilverTrace().start()
