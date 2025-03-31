import React, { useState } from 'react';
import { Upload, FileText, Activity, User, Shield, Brain } from 'lucide-react';

interface Symptom {
  id: string;
  name: string;
}

function App() {
  const [selectedSymptoms, setSelectedSymptoms] = useState<string[]>([]);
  const [uploadedFiles, setUploadedFiles] = useState<File[]>([]);

  const commonSymptoms: Symptom[] = [
    { id: 'fever', name: 'Fever' },
    { id: 'cough', name: 'Cough' },
    { id: 'fatigue', name: 'Fatigue' },
    { id: 'headache', name: 'Headache' },
    { id: 'nausea', name: 'Nausea' },
  ];

  const handleSymptomToggle = (symptomId: string) => {
    setSelectedSymptoms(prev =>
      prev.includes(symptomId)
        ? prev.filter(id => id !== symptomId)
        : [...prev, symptomId]
    );
  };

  const handleFileUpload = (event: React.ChangeEvent<HTMLInputElement>) => {
    if (event.target.files) {
      setUploadedFiles(Array.from(event.target.files));
    }
  };

  return (
    <div className="min-h-screen bg-gradient-to-br from-blue-50 to-indigo-50">
      <nav className="bg-white shadow-md">
        <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-4">
          <div className="flex items-center justify-between">
            <div className="flex items-center">
              <Brain className="h-8 w-8 text-indigo-600" />
              <span className="ml-2 text-xl font-semibold text-gray-900">MediAI Diagnosis</span>
            </div>
          </div>
        </div>
      </nav>

      <main className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8">
        <div className="grid grid-cols-1 md:grid-cols-3 gap-8">
          {/* System Architecture Overview */}
          <div className="col-span-3 bg-white rounded-lg shadow-md p-6 mb-8">
            <h2 className="text-2xl font-bold text-gray-900 mb-4">System Architecture</h2>
            <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
              <ArchitectureCard
                icon={<User className="h-6 w-6" />}
                title="User Interface"
                description="Web/mobile interface for symptom input and report uploads"
              />
              <ArchitectureCard
                icon={<Shield className="h-6 w-6" />}
                title="API Gateway"
                description="Secure request handling and authentication"
              />
              <ArchitectureCard
                icon={<Brain className="h-6 w-6" />}
                title="AI Engine"
                description="ML-powered diagnosis system"
              />
            </div>
          </div>

          {/* Symptom Selection */}
          <div className="bg-white rounded-lg shadow-md p-6">
            <div className="flex items-center mb-4">
              <Activity className="h-6 w-6 text-indigo-600" />
              <h2 className="text-xl font-semibold text-gray-900 ml-2">Symptoms</h2>
            </div>
            <div className="space-y-3">
              {commonSymptoms.map(symptom => (
                <label
                  key={symptom.id}
                  className="flex items-center space-x-3 cursor-pointer"
                >
                  <input
                    type="checkbox"
                    checked={selectedSymptoms.includes(symptom.id)}
                    onChange={() => handleSymptomToggle(symptom.id)}
                    className="form-checkbox h-5 w-5 text-indigo-600 rounded"
                  />
                  <span className="text-gray-700">{symptom.name}</span>
                </label>
              ))}
            </div>
          </div>

          {/* File Upload */}
          <div className="bg-white rounded-lg shadow-md p-6">
            <div className="flex items-center mb-4">
              <Upload className="h-6 w-6 text-indigo-600" />
              <h2 className="text-xl font-semibold text-gray-900 ml-2">Medical Reports</h2>
            </div>
            <div className="border-2 border-dashed border-gray-300 rounded-lg p-6 text-center">
              <input
                type="file"
                multiple
                onChange={handleFileUpload}
                className="hidden"
                id="file-upload"
              />
              <label
                htmlFor="file-upload"
                className="cursor-pointer inline-flex items-center justify-center px-4 py-2 border border-transparent text-sm font-medium rounded-md text-white bg-indigo-600 hover:bg-indigo-700"
              >
                Upload Files
              </label>
              <p className="mt-2 text-sm text-gray-500">
                Upload medical reports, test results, or images
              </p>
            </div>
            {uploadedFiles.length > 0 && (
              <div className="mt-4">
                <h3 className="text-sm font-medium text-gray-700 mb-2">Uploaded Files:</h3>
                <ul className="space-y-2">
                  {uploadedFiles.map((file, index) => (
                    <li key={index} className="flex items-center text-sm text-gray-600">
                      <FileText className="h-4 w-4 mr-2" />
                      {file.name}
                    </li>
                  ))}
                </ul>
              </div>
            )}
          </div>

          {/* Results Panel */}
          <div className="bg-white rounded-lg shadow-md p-6">
            <div className="flex items-center mb-4">
              <Brain className="h-6 w-6 text-indigo-600" />
              <h2 className="text-xl font-semibold text-gray-900 ml-2">AI Diagnosis</h2>
            </div>
            <div className="text-center py-8">
              <button
                className="px-6 py-3 bg-indigo-600 text-white rounded-lg hover:bg-indigo-700 transition-colors"
                onClick={() => alert('AI Diagnosis processing...')}
              >
                Generate Diagnosis
              </button>
            </div>
          </div>
        </div>
      </main>
    </div>
  );
}

function ArchitectureCard({ icon, title, description }: {
  icon: React.ReactNode;
  title: string;
  description: string;
}) {
  return (
    <div className="border border-gray-200 rounded-lg p-4">
      <div className="flex items-center mb-2">
        <div className="text-indigo-600">{icon}</div>
        <h3 className="ml-2 text-lg font-medium text-gray-900">{title}</h3>
      </div>
      <p className="text-sm text-gray-500">{description}</p>
    </div>
  );
}

export default App;[0, 1])
plt.legend(loc='lower right')
plt.show()
